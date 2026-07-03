# Bomba — Resgate em Alto-Mar

Recriação jogável no navegador do jogo **Bomba**, publicado na revista
*Micro Sistemas* nº 56 (maio/1986), por **Hênio de Araújo Bezerra** e
**Jodrian Soares Amorim**.

A matéria original trazia duas versões. Esta recriação é baseada **na versão
para TRS-80 Color (Color 64), em Extended Color BASIC** (páginas 38 e 39 da
revista) — não na versão ZX81/TK85.

## Como jogar

Abra **`index.html`** em qualquer navegador moderno e clique em
**"LIGAR O COLOR 64"** (o clique também ativa o som). Não precisa de servidor
nem de dependências.

A experiência reproduz o Color 64 real rodando o programa: tela de texto de
32 colunas × 16 linhas (caracteres pretos sobre verde, maiúsculas), telas
gráficas PMODE 256×192 com pixels nítidos, e os sons `PLAY`/`SOUND` do
listing via Web Audio (onda quadrada). O jogo abre com o telegrama da missão
digitado letra a letra (na convenção telegráfica da época: VG = vírgula,
PT = ponto), mostra o esquema das bombas no corte do navio e então pergunta
`DIGA QUAL A BOMBA QUE VOCE QUER COMECAR`.

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
- **R** — pede um relatório (tempo, bombas, quantia, suborno, avarias)
- **S** — fala com o informante (suborno); ele conhece um fio-armadilha da bomba
  atual e pode aceitar ou recusar a quantia oferecida. Atenção: como no
  original, a quantia oferecida é debitada **mesmo quando ele recusa** — e o
  suborno bem-sucedido só acontece uma vez por partida.
- **D** — desistir
- Há um teclado auxiliar na página para jogar no celular/tablet.

Os fios são numerados na tela de 0 (topo) a 9 (base) pela coluna de dígitos ao
lado do painel — desenhada pelas cadeias `DRAW` originais (linhas 380–390). É
por esse número que o informante identifica um fio-armadilha.

A pontuação é feita em dinheiro: cada fio cortado e cada bomba desarmada rendem,
explosões e subornos custam.

## Arquivos

- **`index.html`** — o jogo recriado (HTML + CSS + JavaScript, arquivo único).
- **`bomba_trscolor.bas`** — transcrição da listagem em Extended Color BASIC das
  páginas 38–39 da revista, revisada a partir de uma digitalização de alta
  resolução. Inclui as instruções gráficas (`DRAW`, `LINE`, `CIRCLE`, `PAINT`)
  do navio, da bomba, do alicate e do painel de fios.

## Fidelidade ao original

O `bomba_trscolor.bas` é a **fonte da verdade**: tudo o que o `index.html`
exibe (textos, gráficos e sons) sai das cadeias e comandos da listagem.

- **Textos**: todas as mensagens (`PRINT`, `INPUT`, `ZY$` etc.) são literais —
  sem acentos, em maiúsculas, com os formatos `PRINT USING` ("## MIN E ## SEG")
  e as zonas de vírgula do BASIC. Minúsculas ("britania", "ufrn") aparecem em
  vídeo inverso, como no CoCo.
- **Gráficos**: um interpretador dos comandos do TRS-80 Color (`PMODE`, `PCLS`,
  `COLOR`, `LINE`, `CIRCLE`, `PAINT`, `DRAW`, `GET`/`PUT`) executa as cadeias
  originais: o esquema do navio em corte com os números das bombas (220–310),
  o painel de desarme com o rótulo estilizado e o alicate (360–410), os cortes
  com cachos (430), as avarias após cada explosão (110–170), o aviso gráfico do
  fio conjugador (770–780) e o pisca de tela da explosão (`SCREEN 1,S`).
- **Sons**: `PLAY` e `SOUND` interpretados via Web Audio (onda quadrada):
  o clique do telegrama (`V29L25501AB`), os bipes da abertura, o tiro da
  explosão (`O1;L60;V31;C`) e a marcha fúnebre do naufrágio (linhas 740–750).
- **Lógica**: geração e conjugação dos fios (`B(n,0..2)` ativos, `B(n,3..4)`
  armadilha, `B(n,5)` conjugador), renumeração ao cortar o conjugador
  (790–810), condições de naufrágio (680–710), temporizador de 5 min
  (`TIMER>=18000`), suborno debitado mesmo na recusa (610/630), relatório com
  tempo ao vivo (590) e pontuação integral (35/200/bônus/penalidades/`Q=Q+7`).

Os `POKE`s do listing (65495/65494 = velocidade do clock; 136/137/1271 =
cursor) não afetam o modo de vídeo e por isso não têm efeito visual aqui.
