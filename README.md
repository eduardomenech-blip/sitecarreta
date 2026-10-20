# Carretinhas Dutra — Locação de Carretinhas

Site de locação de carretinhas e reboques: catálogo da frota, cálculo de preço em tempo real e
reserva online gravada em banco de dados, com confirmação pelo WhatsApp.

## Funcionalidades

- **Catálogo** com 5 modelos (pequena, média com grade, baú fechada, reboque para moto, carreta para barco),
  capacidade, dimensões e preços por diária e por semana.
- **Reserva online**: escolha do modelo, datas de retirada/devolução, cálculo automático do valor
  (tarifa semanal aplicada a partir de 7 dias) e verificação de conflito de datas por carretinha.
- **Confirmação pelo WhatsApp** com mensagem pronta contendo o número da reserva.
- Seções "Como funciona", vantagens, dúvidas frequentes e botão flutuante de WhatsApp.

## Tecnologias

- TanStack Start (React 19, Vite) + Tailwind CSS 4
- Netlify Database (Postgres) com Drizzle ORM
- Netlify Image CDN para servir as fotos otimizadas em WebP

## Rodando localmente

```bash
pnpm install
netlify dev
```

## Personalização

Telefone, WhatsApp, endereço e horário ficam em `empresa` em `src/data/carretas.ts`.
Modelos e preços da frota ficam no array `carretas` do mesmo arquivo.

## Próximos passos sugeridos

- Painel administrativo protegido (Netlify Identity) para ver, confirmar e cancelar reservas.
- Notificação por e-mail/WhatsApp para a empresa a cada nova reserva.
- Calendário de disponibilidade por modelo.
