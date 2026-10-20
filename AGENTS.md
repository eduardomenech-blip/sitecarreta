# AGENTS.md

Site de locação de carretinhas ("Carretinhas Dutra"), em português (pt-BR). TanStack Start + Tailwind 4,
deploy no Netlify.

## Estrutura

```
db/schema.ts                    Tabela `reservas` (Drizzle). Fonte da verdade do schema.
db/index.ts                     Cliente Drizzle (drizzle-orm/netlify-db, sem connection string).
drizzle.config.ts               Migrations saem em netlify/database/migrations (aplicadas no deploy).
src/data/carretas.ts            Frota, preços, dados da empresa e helpers (calcularValor, diasEntre, brl, cdn).
src/server/reservas.ts          Server function `criarReserva` (validação zod + checagem de conflito + insert).
src/components/Header.tsx       Header fixo + Logo.
src/components/Catalogo.tsx     Cards da frota; botão "Reservar" seleciona o modelo e rola até o formulário.
src/components/Reserva.tsx      Formulário de reserva + resumo com valor estimado.
src/routes/index.tsx            Página única (hero, como funciona, catálogo, reserva, vantagens, FAQ, rodapé).
public/img/                     Fotos geradas por IA; sempre servidas via helper `cdn()` (Netlify Image CDN).
```

## Convenções e decisões

- Toda a copy é em português; nomes de domínio também (carreta, reserva, retirada, devolucao).
- A frota é estática em `src/data/carretas.ts`; o valor da reserva é recalculado no servidor
  (nunca confiar no valor do cliente). Regra: dias × diária. Hoje há um único modelo (`dutra`, R$ 100/dia, foto real em `public/img/carretinha-dutra.jpg`).
- Conflito de datas: uma reserva não cancelada que se sobreponha ao período bloqueia a mesma carretinha.
- Status da reserva: `pendente` (padrão), futuramente `confirmada` / `cancelada`.
- Paleta e fontes definidas em `@theme` em `src/styles.css` (asfalto, laranja, areia; Barlow / Barlow Condensed).
- Mudou o schema? Rode `npx drizzle-kit generate --name <nome>`; nunca aplique migrations manualmente.
- Telefone, endereço (Santa Isabel - SP) e horário (seg a sáb, 6h–18h) em `empresa` são os dados reais informados pelo dono.
