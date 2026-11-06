# otx-motor-ps2

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
| 0.1.2 | Pelo launcher, o desenho volta a ter thread própria (sem a espera pela placa de vídeo a cada quadro). Sprites com U/V no canto do pixel, como no PS2 (reduções e ampliações de imagem certas; acaba a faixa verde no fim da tela do God of War II). |
| 0.1.1 | Gerador sem Python: as ferramentas viraram um único `otx_ferramentas.exe`. Variante SSE4 de verdade, sem nenhuma instrução AVX. |
| 0.1.0 | Primeira versão: tradutor, runtime e IOP próprios. |

---

*English:* PS2 recompilation engine used by otavix010's PC ports. Each port's `gerar.ps1` downloads it, checks its SHA-256 and uses it automatically. No game code or data here. Third-party notices are in `TERCEIROS.txt`.
