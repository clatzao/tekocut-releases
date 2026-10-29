# TekoCut

Editor de vídeo para Windows que faz tudo no seu computador: **sem conta, sem plano, sem créditos e sem nada atrás de paywall.** Seus vídeos, projetos e exportações nunca saem da sua máquina.

Este repositório guarda só os **instaladores e as atualizações automáticas**. O código-fonte é privado.

## ⬇️ Baixar

**[Baixar o TekoCut para Windows (TekoCut-Setup.exe)](https://github.com/clatzao/tekocut-releases/releases/latest/download/TekoCut-Setup.exe)**

Esse link sempre baixa a versão mais recente (cerca de 250 MB). Versões anteriores e o histórico de mudanças estão em [Releases](https://github.com/clatzao/tekocut-releases/releases).

### Requisitos

| | |
| --- | --- |
| Sistema | Windows 10 ou 11, 64 bits |
| Espaço | cerca de 800 MB para o programa, mais espaço para as cópias de edição dos seus vídeos |
| Vídeo | uma placa ou chip gráfico com WebGL2 (praticamente qualquer um dos últimos 10 anos). Sem ele, o app funciona, mas sem efeitos, máscaras, chroma key e correção de cor avançada |
| Internet | não é necessária; só é usada para procurar atualizações |

O FFmpeg já vem dentro do instalador. Não é preciso instalar mais nada.

## Android

**[Baixar o TekoCut para Android (TekoCut.apk)](https://github.com/clatzao/tekocut-releases/releases/latest/download/TekoCut.apk)** · Android 10 ou mais novo

O editor completo no celular, com a tela pensada para o toque:
- como nos editores de celular: o cursor fica parado no meio e a linha do tempo desliza por baixo (arraste para andar no tempo, pinça para zoom);
- toque num clipe e a barra de baixo vira as ferramentas dele (Dividir, Velocidade, Volume, Animação, Ajustar, Filtros, Espelhar, Girar, Congelar…); a seta volta;
- o + no fim dos clipes adiciona mídia; os painéis sobem de baixo e fecham no ✓;
- segure um clipe para arrastar, dois dedos na imagem para mudar tamanho e girar;
- textos, legendas, efeitos, filtros, transições, animações, adesivos, sons, quadros-chave, máscaras, chroma key e o resto do editor;
- **legendas automáticas** no próprio celular (o modelo Whisper é baixado uma vez, 41 ou 77 MB);
- gravar narração, filmar ou tirar foto direto para o projeto, remover o fundo de fotos;
- exportar em MP4, MOV, HEVC (se o celular tiver o codificador), GIF, WAV e MP3 para a galeria;
- atualizações dentro do app (Configurações > Atualizações).

Não existem no celular: manter o tom na velocidade, câmera lenta suave, reduzir ruído, melhorar voz e mudar voz,
estabilizar, reverter, clipe composto e controle por IA (precisam do FFmpeg ou de um PC).

Para instalar, abra o APK no celular e permita **instalar apps desta fonte** quando o Android pedir.
O app ainda não foi testado em muitos celulares: avise se algo não funcionar no seu.

## Instalar

1. Baixe o `TekoCut-Setup.exe` pelo link acima.
2. Abra o instalador. Como ele não tem assinatura digital paga, o Windows pode mostrar **"O Windows protegeu o computador"**. Clique em **Mais informações** e depois em **Executar assim mesmo**. Isso só acontece na primeira instalação.
3. Escolha o idioma (português ou inglês) e a pasta. O padrão é `%LOCALAPPDATA%\Programs\TekoCut`, e o instalador não pede senha de administrador.
4. O instalador cria atalhos na área de trabalho e no menu Iniciar.

## Atualizações automáticas

- O TekoCut procura versões novas ao abrir e a cada 6 horas.
- Quando há uma, ele baixa em segundo plano e mostra **"O TekoCut x.y.z está pronto — Reiniciar"**. Seu projeto é salvo antes de reiniciar.
- Se você clicar em **Depois**, a atualização é instalada quando você fechar o app.
- Em **Configurações > Geral > Atualizações** você vê a versão instalada e pode procurar atualizações na hora.
- Sem internet, nada acontece; ele tenta de novo mais tarde.

## O que ele faz

### Edição e linha do tempo
- Trilha principal com ímã (fecha os espaços sozinha; dá para desligar), mais trilhas de sobreposição, texto, áudio, efeitos e legendas.
- Dividir (Ctrl+B), apagar à esquerda/direita da agulha (Q/W), cortar, mover, duplicar, copiar e colar, encaixe (snapping), seleção em caixa.
- Agrupar e desagrupar clipes, clipes compostos (com edição por dentro), marcadores, esconder/mostrar clipes (V), vincular o vídeo ao seu som.
- Congelar quadro, espelhar, girar 90°, cortar (crop), reverter, separar cenas automaticamente, marcadores na batida da música.
- Keyframes em posição, escala, rotação, opacidade e volume, com curvas de aceleração editáveis.
- Velocidade constante ou curvas de velocidade, câmera lenta suave, manter o tom da voz ao acelerar.
- Pré-visualização ao passar o mouse na linha do tempo, J/K/L, qualidade da prévia ajustável.
- Desfazer/refazer (200 passos), salvamento automático, histórico de versões com restauração.
- Atalhos de teclado personalizáveis; interface em português ou inglês.

### Imagem e cor
- Vídeos e fotos; transformar, opacidade, modos de mesclagem, máscaras, chroma key (fundo verde).
- Fundo da tela (desfoque, cor ou imagem), formatos 16:9, 9:16, 1:1 e outros.
- Correção de cor: brilho, contraste, saturação, exposição, temperatura, HSL por cor, curvas, rodas de cor, LUTs (.cube), cor automática e "igualar cor".
- Filtros prontos, camada de ajuste, estabilização.
- **Remover o fundo** de pessoas em vídeos e fotos, com pincel para corrigir a borda (o modelo roda no seu PC).

### Efeitos, transições e animações
- Efeitos (vinheta, grão de filme, desfoque, brilho, tremor, separação de cores, pixelado, linhas de TV…) com busca e favoritos.
- Transições (fusão, mergulho no preto, deslizar, cortina, zoom).
- Animações de entrada, saída e combo para clipes, fotos e textos.
- Cada opção mostra uma imagem de exemplo, que se mexe quando você passa o mouse.

### Texto e legendas
- Títulos com fonte, tamanho, cor, contorno, sombra, brilho, texto em curva; suas fontes e seus estilos salvos.
- **Legendas automáticas** com whisper.cpp, rodando no seu PC (veja abaixo).
- Lista de legendas editável, aplicar estilo a todas, destacar palavras-chave, importar e exportar SRT/TXT.
- Edição pelo texto: cortar uma legenda ou uma palavra corta o vídeo junto; remover pausas e palavras de preenchimento ("é…", "tipo").
- As legendas acompanham os cortes do vídeo.

### Áudio
- Volume, fade de entrada e saída, extrair o áudio de um vídeo.
- Gravar narração (com ganho de entrada), normalizar o volume (-14 LUFS), reduzir ruído, melhorar voz, modificador de voz.
- Sua biblioteca de músicas e efeitos sonoros.

### Exportação
- MP4 (H.264 ou HEVC), MOV, GIF, MP3/WAV (só áudio), SRT/TXT (legendas).
- De 480p a 4K, até 60 fps, taxa de bits ajustável, exportar só um trecho (marcar entrada e saída com I e O).
- Codificação pela placa de vídeo quando disponível, com volta automática para o processador.
- Capa do vídeo, e conferência do arquivo exportado (duração e sincronia do som).

### Conteúdo que já vem instalado
- **Efeitos, transições e animações:** 47 efeitos, 42 transições e 48 animações, todos com imagem de exemplo.
- **Filtros e fontes:** 58 filtros e 49 fontes (Google Fonts).
- **Textos e adesivos:** 50 estilos de texto e 101 adesivos (formas, setas, balões, carinhas, clima, natureza, objetos, palavras e pixel art).
- **Sons:** 39 efeitos sonoros e 12 músicas de fundo.
- Tudo foi feito para o TekoCut ou tem licença aberta. As fontes estão listadas em [THIRD-PARTY](https://github.com/clatzao/tekocut-releases/blob/main/THIRD-PARTY.md).

### Pacotes: mais efeitos, transições e animações
- Um arquivo **.tekopack** traz efeitos, transições e animações novos, e pode trazer fontes, LUTs e adesivos.
- Para usar, clique em **Importar pacote…** na aba Efeitos ou Transições, ou vá em **Configurações > Pacotes**. Os itens aparecem nas abas com imagem de exemplo.
- Para começar, baixe o [pacote de exemplo](https://github.com/clatzao/tekocut-releases/releases/download/v1.2.0/example.tekopack): 3 efeitos, 3 transições, 3 animações, uma LUT e um adesivo.
- Para criar os seus, siga o [guia do formato](PACKS.md). Efeitos e transições são GLSL, e as transições usam o mesmo formato do [gl-transitions](https://gl-transitions.com), então dá para aproveitar as de lá (respeitando a licença de cada uma). Animações são quadros-chave em JSON.

### Controle por IA (opcional)
- Em **Configurações > Controle por IA**, o TekoCut abre um servidor MCP local (só em 127.0.0.1, com senha).
- Claude, outros clientes MCP e modelos locais (Ollama) podem editar a linha do tempo, ver quadros e a transcrição, importar e exportar.
- Cada pedido é um passo de desfazer, e exportar ou apagar sempre pede sua confirmação.
- Para clientes que só iniciam programas locais (Claude Desktop), use a ponte em `<pasta de instalação>\resources\mcp-bridge.mjs` (precisa do Node.js). A tela de configuração mostra o comando pronto.

## Legendas automáticas

As legendas são feitas pelo [whisper.cpp](https://github.com/ggml-org/whisper.cpp) no seu PC, sem enviar nada para fora. Elas não vêm no instalador porque são grandes e opcionais:

1. Baixe um modelo `ggml-*.bin` em [huggingface.co/ggerganov/whisper.cpp](https://huggingface.co/ggerganov/whisper.cpp/tree/main). O `ggml-base.bin` (cerca de 150 MB) é um bom começo; os maiores são mais precisos e mais lentos.
2. Baixe o `whisper-cli` em [whisper.cpp > Releases](https://github.com/ggml-org/whisper.cpp/releases) (o zip para Windows x64).
3. No TekoCut, na aba **Legendas**, escolha o modelo e o `whisper-cli.exe`. A escolha fica salva.

Num processador antigo, a transcrição leva cerca de 3 vezes a duração da fala.

## Privacidade

- Tudo é feito e guardado no seu computador: mídia, projetos, legendas, sons e exportações.
- A única conexão que o TekoCut faz é procurar atualizações neste repositório, que baixa só o instalador. Nada seu é enviado.
- No celular, as legendas automáticas baixam o modelo de fala do Hugging Face (huggingface.co) quando você toca em Baixar. O áudio é transcrito no próprio celular.
- O controle por IA só aceita conexões do próprio PC (127.0.0.1) e com senha.

## Onde ficam seus dados

| O quê | Onde |
| --- | --- |
| Programa | `%LOCALAPPDATA%\Programs\TekoCut` (ou a pasta que você escolheu) |
| Projetos, cópias de edição, LUTs, sons, adesivos, configurações | `%APPDATA%\replica-editor` (nome antigo do projeto, mantido para não perder nada) |
| Pasta dos novos projetos | mude em **Configurações > Geral** |

As cópias de edição (versões leves dos seus vídeos, para editar sem travar) podem ser apagadas em **Configurações > Cache**. Elas são refeitas quando um projeto precisar.

## Desinstalar

Em **Configurações do Windows > Aplicativos**, procure **TekoCut** e clique em **Desinstalar**. Seus projetos e configurações **não** são apagados. Para apagá-los também, exclua a pasta `%APPDATA%\replica-editor` depois.

## Limitações conhecidas

- Só para Windows por enquanto.
- Manter o tom funciona em velocidades constantes, mas não em curvas de velocidade nem no J/K/L.
- No J/K/L, só a velocidade normal para frente tem som.
- A remoção de fundo encontra pessoas (melhor com uma ou duas pessoas perto da câmera).
- Efeitos não aceitam keyframes, e animações não podem ser salvas como predefinições suas.
- Ainda não tem: modelos prontos (templates), legendas bilíngues/tradução, texto para fala, separar voz e música, aumentar resolução, reenquadrar automaticamente, rastreamento de movimento e cortes curtos automáticos de vídeos longos.

## Histórico de versões

### 1.5.0 (29/10/2026)
- Android: o editor do celular refeito no jeito dos apps de edição de celular: cursor fixo no meio, linha do tempo deslizando, barra de ferramentas do clipe tocado, + para adicionar mídia, painéis com ✓, barra de reprodução enxuta e o formato (proporção) num painel próprio.

### 1.4.0 (29/10/2026)
- Android: a tela do celular (barra de ferramentas, painéis que sobem de baixo) e os gestos de toque.
- Android: legendas automáticas no celular, com o modelo baixado dentro do app.
- Android: exporta MP3, GIF e HEVC; normalizar volume, marcar batidas e dividir cenas funcionam no celular.
- Android: narração, filmar e fotografar direto para o projeto, remover o fundo de fotos, adesivos e sons que já vêm no app.
- Android: ícone, tela de abertura e atualizações dentro do app.

### 1.3.0 (29/10/2026)
- Muito mais conteúdo, tudo feito para o TekoCut ou com licença aberta:
  - 47 efeitos, 42 transições e 48 animações novos;
  - 58 filtros;
  - 49 fontes do Google Fonts;
  - 50 estilos de texto;
  - 101 adesivos;
  - 39 efeitos sonoros e 12 músicas de fundo.

### 1.2.0 (29/10/2026)
- Primeira versão de Android (prévia), em [TekoCut.apk](https://github.com/clatzao/tekocut-releases/releases/latest/download/TekoCut.apk).
- Pacotes (.tekopack): importe efeitos, transições e animações novos, além de fontes, LUTs e adesivos, num arquivo só. Veja em Configurações > Pacotes.
- Pacote de exemplo e guia para criar os seus.

### 1.1.1 (29/10/2026)
- Ao diminuir a janela, os painéis se ajustam em vez de serem cortados; a prévia sempre tem lugar, e os tamanhos que você escolheu voltam quando a janela cresce.
- Os controles da prévia passam para uma segunda linha quando falta espaço.

### 1.1.0 (28/10/2026)
- Imagens de exemplo em efeitos, transições, filtros e animações; elas se mexem ao passar o mouse.
- A animação de abertura volta a aparecer quando as animações do Windows estão desligadas.

### 1.0.0 (28/10/2026)
- Primeira versão instalável: nome TekoCut, ícone em pixel art, animação de abertura (pode ser desligada em Configurações).
- Instalador para Windows e atualizações automáticas.
- Retoque visual: abas sem nomes cortados, mais respiro na grade de mídia, divisórias visíveis na barra da linha do tempo.

## Problemas ou sugestões

Abra uma [issue](https://github.com/clatzao/tekocut-releases/issues) com o que aconteceu, a versão (Configurações > Geral) e, se der, um print.
