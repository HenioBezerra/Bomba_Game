# Bomba — Resgate em Alto-Mar

Recriação jogável no navegador do jogo **Bomba**, publicado na revista
*Micro Sistemas* nº 56 (maio/1986), por **Hênio de Araújo Bezerra** e
**Jodrian Soares Amorim**.

A matéria original trazia duas versões. Esta recriação é baseada **na versão
para TRS-80 Color (Color 64), em Extended Color BASIC** (páginas 38 e 39 da
revista) — não na versão ZX81/TK85.

## Como jogar

Abra **`index.html`** em qualquer navegador moderno. Não precisa de servidor
nem de dependências.

Um grupo de terroristas espalhou cinco bombas no transatlântico inglês
*Britânia*. Você é o perito chamado para desarmá-las antes que o navio afunde —
e tem **5 minutos**.

### Os fios

Cada bomba tem **10 fios**:

| Fios | Quantidade | Efeito ao cortar |
|------|-----------|------------------|
| Armadilha | 2 | a bomba **explode** |
| Ativo | 3 | corte os **três** para **desarmar** |
| Conjugador | 1 | desliga a conjugação do grupo (único fio cuja natureza é avisada) |
| Neutro | 4 | nada acontece |

### Conjugação

As bombas **1 e 2** começam conjugadas entre si; as bombas **3, 4 e 5** também.
Bombas conjugadas têm a *mesma* fiação — descobrir uma revela as outras do
grupo. Ao cortar o **fio-conjugador** de uma bomba, as demais do grupo são
*renumeradas* (recebem nova fiação, ainda iguais entre si).

### O navio afunda se…

- a bomba **nº 3** explodir; **ou**
- a bomba **nº 2** e qualquer outra explodirem; **ou**
- **três** bombas quaisquer explodirem; **ou**
- o tempo de 5 minutos acabar com alguma bomba restante.

### Controles (como na versão Color)

- **↑ / ↓** — movem o alicate entre os fios
- **←** — corta o fio selecionado
- **R** — pede um relatório (tempo, bombas, quantia, avarias)
- **S** — fala com o informante (suborno); ele conhece um fio-armadilha da bomba
  atual e pode aceitar ou recusar a quantia oferecida. O suborno bem-sucedido só
  acontece uma vez por partida.
- **D** — desistir

Também é possível clicar nas bombas e nos fios com o mouse.

A pontuação é feita em dinheiro: cada fio cortado e cada bomba desarmada rendem,
explosões e subornos custam.

## Arquivos

- **`index.html`** — o jogo recriado (HTML + CSS + JavaScript, arquivo único).
- **`bomba_trscolor.bas`** — transcrição, em melhor esforço, da listagem em
  Extended Color BASIC das páginas 38–39 da revista, usada como referência para
  reconstruir a lógica. Por se tratar de uma digitalização de 1986, alguns
  caracteres das densas instruções gráficas (`DRAW`, `LINE`, `CIRCLE`, `PAINT`)
  podem conter imprecisões; a **lógica de jogabilidade**, contudo, foi
  reconstruída fielmente (geração e conjugação dos fios, condições de naufrágio,
  temporizador de 5 min via `TIMER>=18000`, informante/suborno, relatório e
  pontuação).
