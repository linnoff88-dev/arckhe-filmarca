# FALHAS — filmarca

| data | o que quebrou | menor correçêo | prompt \| infra |
|---|---|---|---|
| 2026-10-05 | Palavra partida no meio no 1:1 ("Comunidad/e") passou na validaçêo e foi ao MP4 | Validar também o 1:1 + medir quebra de palavra por Range.getClientRects; regra no prompt da cena | prompt + infra |
| 2026-10-05 | IA usou `{{itens.0}}` e a validaçêo recusou (só aceitava chave simples) | Aceitar caminho com ponto no preenchimento e na validaçêo | prompt |
| 2026-10-05 | Validaçêo dava "nenhum texto visível" em cenas boas: #root com altura 0 fora do runtime HyperFrames | `html,body{width:100%;height:100%}` na composiçêo | infra |
| 2026-10-05 | Validaçêo travava sem erro: `page.evaluate` devolvendo a Timeline do GSAP (objeto circular) | Funçêo do evaluate sem retorno (`{ tl.seek(t) }`) | infra |
| 2026-10-05 | Logo errado (banner do ARCKHÉ.VIP) no ARCKHÉ AI | Descartar imagem com link para outro domínio; sem logo, gerar logotipo em texto | infra |
