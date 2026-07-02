# CLAUDE.md

Orientações para o Claude Code neste repositório.

## Idioma

- **Todas as mensagens ao usuário devem ser em português do Brasil**, incluindo
  as mensagens intermediárias (explicações de progresso, resumos parciais,
  perguntas, avisos e a resposta final). Não use inglês nas respostas ao
  usuário.
- Isso vale apenas para a comunicação com o usuário. Código, nomes de
  variáveis, mensagens de commit e demais artefatos seguem as convenções já
  existentes no projeto.

## Sobre o projeto

Recriação para navegador do jogo **Bomba — Resgate em Alto-Mar** (revista Micro
Sistemas nº 56, maio/1986), versão TRS-80 Color em Extended Color BASIC.

- `index.html` — o jogo (HTML + CSS + JavaScript, arquivo único), com um
  interpretador dos comandos gráficos do TRS-80 Color que executa as cadeias
  `DRAW`/`LINE`/`CIRCLE`/`PAINT` da listagem original.
- `bomba_trscolor.bas` — transcrição de referência da listagem (págs. 38–39).
- `README.md` — regras, controles e notas sobre as fontes.
