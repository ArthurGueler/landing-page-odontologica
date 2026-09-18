# V2 — Dra. Jessica Moreira

Evolução editorial da V1. **Pasta autônoma**: tem o próprio `index.html` e a própria cópia dos
assets, sem nenhuma referência à pasta da V1. Nada aqui afeta a versão original.

```
v2/index.html     → página completa (HTML, CSS e JS no mesmo arquivo)
v2/assets/        → cópia própria das imagens + logo-claro.png (novo)
```

| | V1 | V2 |
|---|---|---|
| Arquivo | `../index.html` | `index.html` |
| Assets | `../assets/` | `v2/assets/` (cópia independente) |
| Abrir | dois cliques em `index.html` da raiz | dois cliques neste `index.html` |
| Comparar | abra `../comparar.html` — mostra as duas lado a lado | |

## Direção da V2

“Odontologia humana + precisão + elegância editorial.”

**Assinatura gráfica**: um arco fino e assimétrico — nunca uma boca, nunca um dente. Definido uma
única vez como `<symbol id="arc-solid">` / `<symbol id="arc-line">` e reutilizado por toda a página:
rótulos de seção, números dos tratamentos, faixa de credenciais, manifesto, horários e rodapé.
A variante `arc-line` se desenha sozinha ao entrar na tela.

**Geometria do arco** virou sistema, com recortes derivados em vez de repetição literal:
retrato do hero com arco no topo, foto do consultório com arco invertido (embaixo), mapa emoldurado
com a mesma curva, círculo de contorno no bloco de convite.

**Paleta** em tokens (`--color-*`), centralizada no `:root`:
marfim `#FBF7F3` · areia `#F4EBE5` · grafite azulado `#20242A` · rosé `#C97B86` (texto: `#9C5763`).

> Sobre o verde mencionado no briefing: a logo da Dra. Jessica **não tem verde** — ela é rosa +
> grafite. Em vez de inventar uma terceira cor, a V2 fica na dupla real da marca. Se um dia entrar
> verde na identidade, basta acrescentar um token.

**Tipografia**: Fraunces variável usando os eixos `SOFT` e `WONK` — o `WONK` é o que dá o swash
característico ao itálico de “funciona”, “em detalhe”, “próximo”, “conversar”. É um detalhe que
nenhum template tem, porque exige pedir o eixo na URL da fonte.

## Refinamento mobile

O mobile foi tratado como composição própria, não como o desktop empilhado. Todo o CSS de
celular vive em media queries no fim da folha, sob o comentário `REFINAMENTO MOBILE` —
o desktop (acima de 940px) não é tocado por nenhuma delas.

**Breakpoints** (poucos e por conteúdo, não por aparelho):

| faixa | o que muda |
|---|---|
| `max-width: 940px` | composição mobile inteira: hero recomposto, tokens de ritmo, tipografia, toque |
| `max-width: 700px` | tratamentos passam de duas colunas para coluna única |
| `max-width: 380px` | colunas mais estreitas, horários sem linha pontilhada |
| `orientation: landscape` + `max-height: 520px` | hero encurtado para caber deitado |
| `hover: none` | hover deixa de ser fonte de informação; entram estados `:active` |

**Hero no celular** — composição própria, montada por `order` (o desktop segue igual):

```
header compacto (~64px)
  eyebrow discreto     JACARAÍPE · SERRA — ES
  headline             Um sorriso que / funciona / e te representa.
  apoio curto          duas linhas
  CTA + Ver tratamentos  (lado a lado quando cabe)
  fotografia           começa por volta de 420px do topo
```

Escalas do hero mobile:

| elemento | valor |
|---|---|
| header | 64–68px de altura, logo 40px, CTA do topo 44px |
| headline | `clamp(35px, 10.6vw, 50px)`, `line-height: .98`, quebras fixas em três linhas |
| apoio | 15,5px, no máximo `34ch` — o trecho longo (`.lede-extra`) só aparece no desktop |
| CTA | 54px de altura, 15,5px de fonte |
| foto | `aspect-ratio: 5/5.6`, teto de `min(46svh, 400px)`, arco `clamp(76px, 24vw, 130px)` |

Telas baixas (`max-height: 700px`, como o iPhone SE) têm um degrau a menos em tudo, para a
dobra continuar entregando header + headline + CTA + começo da foto.

**Composição da hero e transição para o site** (última passagem):
CTA e "Ver tratamentos" viraram um bloco de ações (16px entre eles); o sublinhado do link
acompanha só o rótulo, sem o traço solto sob a seta; a foto encolheu para `aspect-ratio: 1/1.02`
com teto de `min(41svh, 352px)` e subiu no fluxo; a lista de especialidades virou faixa editorial
colada ao fim da foto, sem o CRO/EPAO que se repetia logo abaixo; e a faixa institucional foi
refeita em quatro níveis — label miúdo, nome em Fraunces itálico, credencial e "atendemos aos
domingos" com um traço rosé — sobre um degradê suave que marca o fim da hero.
`scroll-padding-top` (78px no mobile, 132px no desktop) impede que âncoras parem atrás do header.

**Passagem de refino das demais seções** (tudo abaixo da hero):
separadores da ficha viraram `·` presos ao item anterior (não abrem mais linha sozinhos);
a faixa de credenciais ganhou hierarquia — o nome em Fraunces itálico, registros abaixo em
caixa-alta miúda; tratamentos ~15% mais densos; legenda da foto encurtada no celular
(`.cap-extra`); assinatura da Dra. com separadores; kicker do FAQ com `letter-spacing` menor
para não estourar em 320px. A página mobile saiu de 9316px para ~8050px.

**Ritmo vertical** por tokens: `--flow-xs/sm/md/lg`. A hierarquia escolhe o degrau, mas todos
os degraus vêm do mesmo sistema.

**Imagens responsivas**: cada foto tem versão `-760` e as logos versão `-360`, servidas por
`srcset`/`sizes`. No celular a página carrega ~200 KB a menos de imagem.

**Detalhes de toque**: nenhum alvo clicável abaixo de 44px; `env(safe-area-inset-*)` no header,
no rodapé e no botão flutuante; `svh` em vez de `vh`; o botão de WhatsApp recolhe ao chegar na
área de contato, para nunca cobrir os CTAs reais; o mapa tem um escudo que libera o iframe no
primeiro toque, para o gesto de rolar não ficar preso dentro dele.

**Navegação**: no celular o menu não vira hambúrguer. Os três links dão lugar ao único botão que
converte — Agendar — e a navegação acontece pelo scroll. Um hambúrguer aqui seria convenção sem
função, já que a página é curta e linear.

## Como editar

Telefone e Instagram ficam num único lugar, no fim do arquivo:

```js
const CONFIG = {
  whatsapp: "5527981919841",
  instagram: "drajessicamoreira"
};
```

Restam 4 marcadores `EDITAR` no arquivo: formação/especializações da Dra., convênios aceitos,
formas de pagamento e o domínio final (canonical).

## Fotografia

O layout está preparado para um ensaio profissional. Para trocar, substitua o arquivo em
`assets/` mantendo o nome — o recorte é feito por CSS (`object-fit`/`object-position`), não
depende do enquadramento original.

| Arquivo | Onde | Proporção ideal |
|---|---|---|
| `dra-jessica.jpg` | retrato do hero | vertical 4:5 — **substituir por retrato com o rosto visível** quando houver ensaio |
| `consultorio.jpg` | seção Sobre | quadrada 1:1 |
| `logo.png` | header | horizontal, fundo transparente |
| `logo-claro.png` | rodapé escuro | mesma logo, grafite trocado por marfim |
| `og.jpg` | preview de link | 1200×630 |

A foto atual do hero mostra a Dra. de máscara. Mantida temporariamente, como combinado — o bloco
`<figure class="portrait">` é uma única troca de `<img>`.

## Acessibilidade e performance

- Skip link, `focus-visible` em rosé, navegação por teclado, `<details>` nativo no FAQ
- Reveals só existem com JS ativo (classe `.js` no `<html>`): sem JS, nada fica invisível
- `prefers-reduced-motion` desliga animação, desenho de traço e a animação do accordion
- Sem bibliotecas — nenhuma dependência nova; tudo CSS nativo + ~60 linhas de JS
- Imagens com `width`/`height` (evita CLS), `loading="lazy"` fora do hero, `fetchpriority="high"` no retrato

## Conformidade (CFO)

Mesmos cuidados da V1: nenhuma promessa de resultado, nenhum preço como chamariz, nenhum
depoimento ou número inventado, RT com CRO 8271 ES e EPAO-2513 no rodapé.
