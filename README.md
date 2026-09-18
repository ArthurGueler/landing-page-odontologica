# Landing page — Dra. Jessica Moreira

Site de uma página só, focado em levar quem chega do Instagram direto para o WhatsApp.
Não precisa instalar nada: é um `index.html` puro. Basta abrir no navegador com dois cliques.

```
index.html      → a página inteira (HTML, CSS e JS no mesmo arquivo)
assets/         → imagens já otimizadas usadas pelo site
originais/      → PNGs originais enviados (NÃO publicar — ~4 MB, só backup)
README.md       → este guia
```

## Dados já configurados

| | |
|---|---|
| WhatsApp | (27) 98191-9841 |
| Instagram | @drajessicamoreira |
| Endereço | Av. Minas Gerais, 1026 — Jacaraípe, Serra/ES, 29175-608 |
| Horários | Dom e Seg 09–18h · Ter e Qua 14:30–18h · Qui e Sex 10:30–18h · Sáb fechado |
| Registro | CRO 8271 ES · EPAO-2513 (no rodapé, como exige o Conselho) |

A tabela de horários **destaca sozinha o dia de hoje** — quem abre no domingo vê "Domingo · hoje"
em rosa. O domingo aberto virou argumento de venda: aparece na faixa abaixo do topo e no FAQ.

## O que ainda falta (opcional)

Abra o `index.html` num editor de texto e procure por `EDITAR` — restam apenas 3 pontos:

1. **Seção "Sobre"** — formação, especializações e tempo de atuação da Dra.
2. **FAQ** — quais convênios são aceitos
3. **FAQ** — formas de pagamento e parcelamento
4. `<link rel="canonical">` — o domínio definitivo, quando houver

Para mudar telefone ou Instagram no futuro, só existe um lugar (no fim do arquivo):

```js
const CONFIG = {
  whatsapp: "5527981919841",
  instagram: "drajessicamoreira"
};
```

## Imagens

As fotos foram redimensionadas e comprimidas (de ~2 MB para ~150 KB cada) para o site abrir rápido
no 4G. Os originais ficaram em `originais/`.

| Arquivo | Onde aparece |
|---|---|
| `assets/logo.png` | Topo do site (a logo substitui o nome escrito) |
| `assets/dra-jessica.jpg` | Retrato do hero, recortado em arco |
| `assets/consultorio.jpg` | Seção "Sobre" |
| `assets/og.jpg` | Preview ao mandar o link no WhatsApp |

Para trocar qualquer uma, basta substituir o arquivo em `assets/` mantendo o mesmo nome.

## Como publicar (grátis)

**Netlify Drop — 30 segundos:**

1. Acesse https://app.netlify.com/drop
2. Arraste a pasta do projeto para a página (pode apagar `originais/` antes, para não subir peso à toa)
3. O link sai na hora (ex.: `nome-aleatorio.netlify.app`)

Depois dá para conectar um domínio próprio (ex.: `drajessicamoreira.com.br`)
em Site settings → Domain management.

Alternativas equivalentes: Vercel, Cloudflare Pages ou GitHub Pages.

## Antes de colocar na bio do Instagram

- [ ] Abrir no celular e clicar em **todos** os botões — cada um abre o WhatsApp com uma mensagem diferente
- [ ] Mandar o link para si mesmo no WhatsApp e ver se o preview (imagem + título) aparece certo
- [ ] Conferir se o mapa está apontando para o endereço certo
- [ ] Rodar o Lighthouse no Chrome (F12 → Lighthouse → Mobile) — a meta é 95+ em tudo

## Observações de conformidade (CFO)

O Código de Ética Odontológica proíbe promessa de resultado, preço usado como chamariz
e "antes e depois" sem contexto clínico. Os textos foram escritos dentro dessas regras,
e o nome da responsável técnica com CRO e EPAO aparece no rodapé, como exigido.
Ao editar os textos, manter esse cuidado.
