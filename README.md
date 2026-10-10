# Project Ravoc

Fixes for the Tibia 15.30 Crystal Server community stack, kept as close to the **official game (global)** as possible.

This repository contains **no custom systems**: only the community base plus corrections that make existing content behave like the official game. Each fix is a **separate commit**, so you can read, cherry-pick or copy just the one you need.

| Folder | Based on | License |
|---|---|---|
| `server/` | [s2leandro155/crystalserver1530ot](https://github.com/s2leandro155/crystalserver1530ot) @ `bced5fcc` (2026-09-01), a 15.30 build of [Crystal Server](https://github.com/zimbadev/crystalserver) | GPL-2.0 (`server/LICENSE`) |
| `client/` | [s2leandro155/CrystalOTC1530](https://github.com/s2leandro155/CrystalOTC1530) @ `b59ae4f` (2026-08-23), based on [OTClient](https://github.com/edubart/otclient) / [OTClient Redemption](https://github.com/mehah/otclient) | MIT (`client/LICENSE`) |

All credit for the base goes to the original authors. The first commit of this repository is the untouched upstream code; everything after it is a fix.

## How the fixes are verified
- Facts come from [TibiaWiki](https://tibia.fandom.com) (quest spoilers, NPC transcripts, item/creature pages) and gameplay videos when the wiki has no numbers.
- Positions are checked against the official map (the same `world.otbm` the base uses).
- Every fix was played and approved in game before being published.
- Values that no public source gives are marked `NOT CONFIRMED` in the code, so they are easy to find and adjust.

## Fixes
See the commit history. Each commit message explains what was wrong, what changed and how to test it.

---

# Project Ravoc (PT-BR)

Correções para o Crystal Server 15.30 da comunidade, o mais fiéis possível ao **Tibia oficial (global)**.

Aqui **não há sistemas customizados**: só a base da comunidade e correções para que o conteúdo existente funcione como no jogo oficial. Cada correção é **um commit separado** — dá para ver, aplicar ou copiar só a que interessa.

A base está creditada na tabela acima (pastas `server/` e `client/`, com as licenças originais). O primeiro commit é o código original, sem alterações; tudo depois dele é correção.

Como as correções são conferidas: fatos da TibiaWiki e de vídeos do jogo, posições conferidas no mapa oficial, e cada correção foi jogada e aprovada antes de publicar. Valores sem fonte pública ficam marcados como `NOT CONFIRMED` no código.
