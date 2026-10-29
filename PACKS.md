# TekoCut packs (.tekopack)

A pack adds **effects, transitions and animations**, and can carry **fonts, LUTs and stickers**, in one file. Import it
in the app with **Import pack…** (Effects or Transitions tab, or Settings > Packs). The example is
[example.tekopack](https://github.com/clatzao/tekocut-releases/releases/download/v1.2.0/example.tekopack).

- Importing a pack with the same `id` again replaces it, so a newer version of a pack updates in place.
- A project names the pack items it uses (`pack:<pack id>:<item id>`). If a pack is removed, those clips play without
  it (an effect is skipped, a transition crossfades) until the pack is added back.
- Fonts, LUTs and stickers go into their own libraries when the pack is imported. Removing the pack keeps them.
- Effects and transitions are GLSL ES 3.00 run by the WebGL2 compositor, in the preview and the export alike. A shader
  that doesn't compile on the computer is listed in Settings > Packs with the compiler's message, and skipped.

## The file

JSON, at most 40 MB:

```json
{
  "format": "tekopack-1",
  "id": "my-pack",
  "name": "My pack",
  "author": "Me",
  "description": "What it brings",
  "effects": [ { "id": "negative", "name": "Negative", "about": "Inverts the colours", "glsl": "..." } ],
  "transitions": [ { "id": "circle-open", "name": "Circle open", "glsl": "..." } ],
  "animations": [ { "id": "bounce-in", "name": "Bounce in", "slot": "in", "keys": [ ... ] } ],
  "fonts": [ { "name": "My Font.ttf", "data": "<base64>" } ],
  "luts": [ { "name": "Warm.cube", "data": "<base64>" } ],
  "stickers": [ { "name": "Star.png", "data": "<base64>" } ]
}
```

- Ids are 1–40 lowercase letters, digits and dashes, unique within their list.
- Names are at most 60 characters, and are shown as written (they aren't translated).
- Every list is optional. Fonts can be TTF, OTF, WOFF or WOFF2; LUTs are `.cube`; stickers are PNG, WebP or GIF.

## Effects

An effect runs over everything drawn below it while its clip plays. Write `vec4 effect(vec2 uv)`:

| you get | meaning |
| --- | --- |
| `uv` | 0..1 across the frame, (0, 0) at the bottom left |
| `getColor(uv)` | the frame so far at `uv` |
| `amount` | the clip's strength, 0..1 (Inspector) |
| `time` | seconds into the effect clip |
| `resolution` | the frame's size in pixels |

```glsl
vec4 effect(vec2 uv) {
  vec4 c = getColor(uv);
  return vec4(mix(c.rgb, 1.0 - c.rgb, amount), 1.0);
}
```

Don't declare `amount`, `time` or `resolution` yourself; they are already there.

## Transitions

A transition mixes the outgoing clip into the incoming one over the cut. It has the same shape as
[gl-transitions](https://gl-transitions.com), so those can be pasted in (keep their licence). Write
`vec4 transition(vec2 uv)`:

| you get | meaning |
| --- | --- |
| `getFromColor(uv)` | the outgoing clip |
| `getToColor(uv)` | the incoming clip |
| `progress` | 0 → 1 across the transition |
| `ratio` | width / height |

Parameters take their value from a comment, as gl-transitions writes them: `uniform float softness; // = 0.08`
(float, int, bool, vec2–vec4).

```glsl
uniform float cells; // = 24.0
float rnd(vec2 p) { return fract(sin(dot(p, vec2(12.9898, 78.233))) * 43758.5453); }
vec4 transition(vec2 uv) {
  vec2 cell = floor(uv * vec2(cells * ratio, cells));
  return rnd(cell) < progress ? getToColor(uv) : getFromColor(uv);
}
```

Without WebGL2 (the 2D fallback), pack transitions crossfade and pack effects are skipped.

## Animations

Keyframes for an `in`, `out` or `loop` animation; `"textOnly": true` lists it for titles only. Each key has `at`
(0..1 through the animation: an in animation ends at rest, an out one starts at rest, a loop is one period) and any of:

| key | meaning | at rest |
| --- | --- | --- |
| `dx`, `dy` | move, as a fraction of the frame (positive `dy` is down) | 0 |
| `scale` | size | 1 |
| `rotation` | degrees | 0 |
| `opacity` | 0..1 | 1 |
| `reveal` | how much of a title shows, 0..1 (typing) | 1 |

Each value moves in a straight line between the keys that give it.

```json
{ "id": "bounce-in", "name": "Bounce in", "slot": "in", "keys": [
  { "at": 0, "dy": 0.35, "opacity": 0 }, { "at": 0.55, "dy": -0.04, "opacity": 1 }, { "at": 0.78, "dy": 0.015 }, { "at": 1, "dy": 0 }
] }
```
