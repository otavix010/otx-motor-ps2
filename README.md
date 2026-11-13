<h1 align="center">otx-motor-ps2</h1>

<p align="center"><i>Motor de recompilação de PS2 dos ports de PC (pacote pré-compilado)</i></p>

<p align="center">
  <a href="https://github.com/otavix010/otx-motor-ps2/releases/latest"><img alt="Versão" src="https://img.shields.io/github/v/release/otavix010/otx-motor-ps2?label=vers%C3%A3o"></a>
  <a href="https://github.com/otavix010/otx-motor-ps2/commits/main"><img alt="Última atualização" src="https://img.shields.io/github/last-commit/otavix010/otx-motor-ps2?label=%C3%BAltima%20atualiza%C3%A7%C3%A3o"></a>
</p>

Motor de recompilação de PS2 usado pelos ports de PC do otavix010. O pacote é pré-compilado e traz:

- `bin\otx_tradutor.exe`: tradutor do código do jogo (MIPS R5900) para C++;
- `bin\otx_ferramentas.exe`: mapa de funções, tabela, remendos, VU1 e extração do disco;
- `lib\avx2` e `lib\sse4`: o runtime (EE, IOP, GS, VU, SPU2 etc.), uma variante para CPUs com AVX2 e outra para CPUs sem;
- `include\` e `cmake\`: o que o build do jogo precisa para ligar o runtime.

Não é preciso baixar nada daqui à mão. O `gerar.ps1` de cada port baixa o pacote da última versão, confere o SHA-256 e usa sozinho.

Este repositório não contém código nem dados de nenhum jogo. Os componentes de terceiros e as licenças deles estão em [TERCEIROS.txt](TERCEIROS.txt). O motor é distribuído de graça para uso com os ports, sem garantia de nenhum tipo.

## Versões

| Versão | O que mudou |
|---|---|
| 0.1.10 | Vídeos (libmpeg): o áudio do PSS também chega ao callback de stream do tipo 3; o God of War II registrava o áudio nesse tipo, ficava sem som no vídeo e pulava o FMV de abertura (Rodes). PS2X_MPEG_AUDIO_TIPOS escolhe os tipos (padrão 123). VU1: o XGKICK em lote dá quantas voltas forem precisas na memória do VU; um pacote maior que ela lia além do fim (0xC0000005 no memcpy). |
| 0.1.9 | Núcleos do processador: o modo automático (PS2X_NUCLEOS=auto, padrão) agora só indica o núcleo preferido de cada thread principal, em vez de prendê-la a ele. Em processadores de 6 núcleos com outros programas abertos, o fps subiu de ~32 para ~50 no God of War (Core i5-11400F). O comportamento antigo continua em PS2X_NUCLEOS=fixo. Na resolução interna, as reduções de imagem são desenhadas em 1x. |
| 0.1.8 | Memory card: o motor cria a pasta do cartão (trabalho\disc\mc0) e avisa no log quando não consegue gravar; antes, sem a pasta, o save ficava só na memória (God of War e God of War II). Resolução interna do GS de 1x a 4x (PS2X_RESOLUCAO; padrão 1x), com o GS na GPU. Aviso na tela enquanto os gráficos são preparados na primeira vez. Registro de quedas com a pilha e o nome das threads. |
| 0.1.7 | Memory card do God of War II funciona (carga LWL/LWR no delay slot do IOP corrigida; sceCdReadClock). Áudio pode ser silenciado nos testes (PS2X_SOM_MUDO) e registro de quedas. |
| 0.1.2 | Pelo launcher, o desenho volta a ter thread própria (sem a espera pela placa de vídeo a cada quadro). Sprites com U/V no canto do pixel, como no PS2 (reduções e ampliações de imagem certas; acaba a faixa verde no fim da tela do God of War II). |
| 0.1.1 | Gerador sem Python: as ferramentas viraram um único `otx_ferramentas.exe`. Variante SSE4 de verdade, sem nenhuma instrução AVX. |
| 0.1.0 | Primeira versão: tradutor, runtime e IOP próprios. |

---

*English:* PS2 recompilation engine used by otavix010's PC ports. Each port's `gerar.ps1` downloads it, checks its SHA-256 and uses it automatically. No game code or data here. Third-party notices are in `TERCEIROS.txt`.
