# ðŸŽ¬ filmarca

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![filmarca: site vira filme](guia/assets/banner.jpg)](https://linnoff88-dev.github.io/

**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

## O que Ã©

O filmarca Ã© uma ferramenta gratuita que transforma o site de uma empresa ou produto num vÃ­deo curto de apresentaÃ§Ã£o da marca. VocÃª informa o endereÃ§o; ele copia as cores, as fontes, o logo e os textos do site, e a inteligÃªncia artificial escreve o roteiro e monta as cenas animadas. Serve para quem precisa de um vÃ­deo para redes sociais ou para o prÃ³prio site e nÃ£o tem editor de vÃ­deo. Roda no seu computador e precisa do Node.js e de uma assinatura do Claude Code ou do Codex, sem pagar API.

**Do site ao filme da marca.** Aponte um endereÃ§o: o filmarca lÃª cores, fontes, logo, textos e prints do site, escreve o roteiro, anima as cenas e entrega o MP4 em 16:9, 9:16 e 1:1, em portuguÃªs, inglÃªs e espanhol. A IA roda pela **sua assinatura** (Claude Code ou Codex), sem chave de API, e o render Ã© local, com o [HyperFrames](https://hyperframes.dev).

## ðŸ“– Guia de uso

Guia completo (landing + passo a passo): **https://linnoff88-dev.github.io/

## Demo

O filme do ARCKHÉ AI, feito pela prÃ³pria ferramenta (8 cenas escritas pela IA, todas aprovadas na conferÃªncia, 2,7 min de ponta a ponta):

[![demo](docs/demo.gif)](docs/demo-pt-16x9.mp4)

[16:9 PT](docs/demo-pt-16x9.mp4) Â· [9:16 PT](docs/demo-pt-9x16.mp4) Â· [16:9 EN](docs/demo-en-16x9.mp4) Â· [16:9 ES](docs/demo-es-16x9.mp4)

## InstalaÃ§Ã£o

Precisa de Node.js 22+, FFmpeg e o Claude Code (`claude`) ou o Codex (`codex`) logado no terminal.

```bash
git clone https://github.com/linnoff88-dev/filmarca
cd filmarca
npm i
npx playwright install chromium
```

## Uso

```bash
# tudo de uma vez (rascunho rÃ¡pido para revisar)
node bin/filmarca.mjs fazer https://seusite.com --out ~/filmes/seusite --duracao 30 --rascunho

# com orientaÃ§Ã£o para o diretor, usando o Codex, jÃ¡ em trÃªs idiomas
node bin/filmarca.mjs fazer https://seusite.com --pedido "lanÃ§amento do plano anual" --motor codex --langs pt,en,es

# etapas soltas sobre a pasta do filme
node bin/filmarca.mjs editar ~/filmes/seusite c3 "o nÃºmero entra contando"
node bin/filmarca.mjs voltar ~/filmes/seusite c3 1
node bin/filmarca.mjs traduzir ~/filmes/seusite --lang en
node bin/filmarca.mjs render ~/filmes/seusite --langs pt,en --trilha musica.mp3
```

`node bin/filmarca.mjs ajuda` lista todos os comandos. A pasta do filme guarda `marca.json`, `roteiro.json`, `cenas/` (com versÃµes), `textos/<idioma>.json`, `revisao.html` e `renders/`.

## Como funciona

1. **DNA do site** (Playwright): cores por papel (fundo, texto, botÃ£o), fontes com os arquivos, logo (ou logotipo em texto gerado), tÃ­tulos, nÃºmeros e prints do topo, de trÃªs faixas e do celular.
2. **Roteiro**: o diretor escreve o conceito e as cenas sÃ³ com fatos do site.
3. **Cenas**: a IA escreve cada cena como HTML + CSS + GSAP seguindo um contrato fechado (medidas relativas ao quadro, textos por marcador `{{chave}}`).
4. **ConferÃªncia**: cada cena roda sozinha no Chromium em 16:9, 9:16 e 1:1. Recusa rede, relÃ³gio, acaso, animaÃ§Ã£o CSS, texto fora do quadro, palavra partida e valores NaN. Recusada, a IA corrige uma vez; se falhar de novo, entra uma cena-modelo.
5. **Render**: uma composiÃ§Ã£o HyperFrames por idioma e formato, `hyperframes lint` e MP4.

## Testes

```bash
npm test
```

## De onde veio a ideia

O mÃ©todo foi inspirado no [Motive](https://github.com/noeltg77/motive). Como ele nÃ£o tem licenÃ§a, o filmarca foi escrito do zero, sem copiar cÃ³digo nem prompts, com IA pela assinatura, HyperFrames no lugar do Remotion e conferÃªncia no navegador nos trÃªs formatos.

## LicenÃ§a

MIT. As fontes embutidas (Inter e Sora) sÃ£o SIL Open Font License. Fontes baixadas de um site servem sÃ³ para o seu render local; nÃ£o as redistribua.

---

Feito pelo [ARCKHÉ AI](https://ARCKHÉ AI).

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>