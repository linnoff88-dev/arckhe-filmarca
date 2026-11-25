# ê°Å¸Å½Â¬ filmarca

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![filmarca: site vira filme](guia/assets/banner.jpg)](https://linnoff88-dev.github.io/

**ê°Å¸â¡Â§ê°Å¸â¡Â· [PortuguêÂªs](README.md) êÂ· ê°Å¸â¡Âºê°Å¸â¡Â¸ [English](README.en.md) êÂ· ê°Å¸â¡Âªê°Å¸â¡Â¸ [EspaêÂ±ol](README.es.md)**

## O que êÂ©

O filmarca êÂ© uma ferramenta gratuita que transforma o site de uma empresa ou produto num vêÂ­deo curto de apresentaêÂ§êÂ£o da marca. VocêÂª informa o endereêÂ§o; ele copia as cores, as fontes, o logo e os textos do site, e a inteligêÂªncia artificial escreve o roteiro e monta as cenas animadas. Serve para quem precisa de um vêÂ­deo para redes sociais ou para o prêÂ³prio site e nêÂ£o tem editor de vêÂ­deo. Roda no seu computador e precisa do Node.js e de uma assinatura do Claude Code ou do Codex, sem pagar API.

**Do site ao filme da marca.** Aponte um endereêÂ§o: o filmarca lêÂª cores, fontes, logo, textos e prints do site, escreve o roteiro, anima as cenas e entrega o MP4 em 16:9, 9:16 e 1:1, em portuguêÂªs, inglêÂªs e espanhol. A IA roda pela **sua assinatura** (Claude Code ou Codex), sem chave de API, e o render êÂ© local, com o [HyperFrames](https://hyperframes.dev).

## ê°Å¸ââ Guia de uso

Guia completo (landing + passo a passo): **https://linnoff88-dev.github.io/

## Demo

O filme do ARCKHê AI, feito pela prêÂ³pria ferramenta (8 cenas escritas pela IA, todas aprovadas na conferêÂªncia, 2,7 min de ponta a ponta):

[![demo](docs/demo.gif)](docs/demo-pt-16x9.mp4)

[16:9 PT](docs/demo-pt-16x9.mp4) êÂ· [9:16 PT](docs/demo-pt-9x16.mp4) êÂ· [16:9 EN](docs/demo-en-16x9.mp4) êÂ· [16:9 ES](docs/demo-es-16x9.mp4)

## InstalaêÂ§êÂ£o

Precisa de Node.js 22+, FFmpeg e o Claude Code (`claude`) ou o Codex (`codex`) logado no terminal.

```bash
git clone https://github.com/linnoff88-dev/filmarca
cd filmarca
npm i
npx playwright install chromium
```

## Uso

```bash
# tudo de uma vez (rascunho rêÂ¡pido para revisar)
node bin/filmarca.mjs fazer https://seusite.com --out ~/filmes/seusite --duracao 30 --rascunho

# com orientaêÂ§êÂ£o para o diretor, usando o Codex, jêÂ¡ em trêÂªs idiomas
node bin/filmarca.mjs fazer https://seusite.com --pedido "lanêÂ§amento do plano anual" --motor codex --langs pt,en,es

# etapas soltas sobre a pasta do filme
node bin/filmarca.mjs editar ~/filmes/seusite c3 "o nêÂºmero entra contando"
node bin/filmarca.mjs voltar ~/filmes/seusite c3 1
node bin/filmarca.mjs traduzir ~/filmes/seusite --lang en
node bin/filmarca.mjs render ~/filmes/seusite --langs pt,en --trilha musica.mp3
```

`node bin/filmarca.mjs ajuda` lista todos os comandos. A pasta do filme guarda `marca.json`, `roteiro.json`, `cenas/` (com versêÂµes), `textos/<idioma>.json`, `revisao.html` e `renders/`.

## Como funciona

1. **DNA do site** (Playwright): cores por papel (fundo, texto, botêÂ£o), fontes com os arquivos, logo (ou logotipo em texto gerado), têÂ­tulos, nêÂºmeros e prints do topo, de trêÂªs faixas e do celular.
2. **Roteiro**: o diretor escreve o conceito e as cenas sêÂ³ com fatos do site.
3. **Cenas**: a IA escreve cada cena como HTML + CSS + GSAP seguindo um contrato fechado (medidas relativas ao quadro, textos por marcador `{{chave}}`).
4. **ConferêÂªncia**: cada cena roda sozinha no Chromium em 16:9, 9:16 e 1:1. Recusa rede, relêÂ³gio, acaso, animaêÂ§êÂ£o CSS, texto fora do quadro, palavra partida e valores NaN. Recusada, a IA corrige uma vez; se falhar de novo, entra uma cena-modelo.
5. **Render**: uma composiêÂ§êÂ£o HyperFrames por idioma e formato, `hyperframes lint` e MP4.

## Testes

```bash
npm test
```

## De onde veio a ideia

O mêÂ©todo foi inspirado no [Motive](https://github.com/noeltg77/motive). Como ele nêÂ£o tem licenêÂ§a, o filmarca foi escrito do zero, sem copiar cêÂ³digo nem prompts, com IA pela assinatura, HyperFrames no lugar do Remotion e conferêÂªncia no navegador nos trêÂªs formatos.

## LicenêÂ§a

MIT. As fontes embutidas (Inter e Sora) sêÂ£o SIL Open Font License. Fontes baixadas de um site servem sêÂ³ para o seu render local; nêÂ£o as redistribua.

---

Feito pelo [ARCKHê AI](https://ARCKHê AI).

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>