# Processo Comercial MX — app interno

Documento interativo do processo comercial da MX Digital Automações: 12 seções + ferramentas
(calculadora de no-show, simulador da meta, reunião guiada com cronômetro, banco de objeções,
gerador de proposta, checklist de onboarding, templates Meta).

Site estático. `index.html` é **autossuficiente** — um único arquivo, sem build, sem dependência
externa. Funciona offline, abre em qualquer navegador, celular ou notebook.

## Estrutura

```
index.html   ← tudo aqui dentro (HTML + CSS + JS + fontes)
```

## Deploy na Vercel

1. Criar repo vazio `app-processo-mx` em github.com/maxwel7639-pixel
2. Liberar o app Claude nesse repo: github.com/settings/installations → app Claude →
   Configure → Repository access → adicionar `app-processo-mx` → Save
3. Push (PowerShell, um comando por vez):

```powershell
cd C:\Users\Digital\Documents\GitHub
mkdir app-processo-mx
cd app-processo-mx
# copiar index.html e README.md para esta pasta
git init
git add .
git commit -m "Processo Comercial MX — app interno"
git branch -M main
git remote add origin https://github.com/maxwel7639-pixel/app-processo-mx.git
git push -u origin main
```

4. vercel.com → Add New → Project → Import Git Repository → `app-processo-mx`
   - Framework: **Other**
   - Build Command / Output Directory: **vazios**
   - Root Directory: **vazio** (o `index.html` já está na raiz — se ficar em subpasta, apontar aqui)

## No celular

Abrir o link da Vercel → menu do navegador → **Adicionar à tela de início**. Abre em tela cheia,
com ícone, sem barra do navegador. As metas de PWA já estão no `<head>`.

## O que fica salvo no aparelho

Só o checklist de onboarding (`localStorage`, chave `mx-processo-onboarding`). Sliders, cronômetro
e proposta são de sessão — recarregar zera. Cada aparelho tem seu próprio estado; não sincroniza.

## Atalhos

- `P` — entra/sai do modo apresentação
- `←` `→` — navega entre as telas (no modo apresentação)
- `Esc` — sai do modo apresentação

## Se for reconstruir no Claude Code

O `index.html` é o **artefato final**, não código-fonte para copiar. Se a ideia for virar app de
verdade (multi-usuário, dados sincronizados, CRM plugado), o caminho é reimplementar as telas em
framework, usando este arquivo como referência visual e de comportamento.

Identidade fixa: fundo `#080808`, dourado `#C9A84C`, texto `#EDEAE4` / `#B4B0A8` / `#6E6A63`,
bordas `#1c1c1c`. Fontes: Inter (corpo) + Cormorant Garamond (títulos e números). Cantos de 2px,
sem sombras, sem gradiente além das barras do gráfico.
