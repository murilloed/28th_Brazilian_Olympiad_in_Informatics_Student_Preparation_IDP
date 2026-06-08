# Lista De 10 Problemas Extremamente Dificeis

## Programacao Universitaria / OBI Nivel Senior

Esta lista foi criada a partir da ementa da Modalidade Programacao, com foco nos topicos mais avancados cobraveis no **Nivel 2 e Nivel Senior**, especialmente os itens marcados como `[P2]`.

Os problemas seguem o modelo das provas de programacao: enunciado contextualizado, entrada/saida formal, restricoes grandes e necessidade de algoritmos eficientes.

## Publico-Alvo

```text
Alunos universitarios
Modalidade Programacao
Nivel Senior
Treino em Python
```

## Observacao

Os problemas abaixo sao intencionalmente mais dificeis que uma lista comum. Eles foram pensados para desenvolver maturidade em:

- analise de complexidade;
- escolha de estrutura de dados;
- modelagem matematica;
- grafos;
- programacao dinamica;
- geometria computacional;
- combinacao de tecnicas.

---

# 1. Arquivos Com Versoes

Um sistema possui `N` arquivos numerados de `1` a `N`. Cada arquivo possui uma prioridade inicial `A_i`.

Voce deve processar `Q` operacoes:

- `1 L R X`: aumentar em `X` a prioridade de todos os arquivos de `L` a `R`;
- `2 L R`: consultar a maior prioridade no intervalo `L` a `R`;
- `3 L R`: consultar a soma das prioridades no intervalo `L` a `R`.

## Entrada

A primeira linha contem `N` e `Q`.

A segunda linha contem `N` inteiros `A_i`.

As proximas `Q` linhas contem uma operacao.

## Saida

Para cada operacao do tipo `2` ou `3`, imprima a resposta.

## Restricoes

```text
1 <= N, Q <= 200000
0 <= A_i, X <= 10^9
1 <= L <= R <= N
```

## Exemplo

Entrada:

```text
5 5
1 2 3 4 5
2 1 5
1 2 4 10
3 1 5
2 3 3
3 2 4
```

Saida:

```text
5
45
13
39
```

## Topicos Da Ementa

- `[P2]` Segment Tree 1D;
- `[P2]` Lazy Propagation;
- Big O;
- trade-off espaco-tempo.

## Dificuldade

Extremamente dificil.

## Ideia Esperada

Usar uma Segment Tree com Lazy Propagation que armazene, para cada no:

- soma do intervalo;
- maximo do intervalo;
- valor pendente de atualizacao.

---

# 2. Pergaminhos E Consultas Imutaveis

Um pergaminho possui `N` numeros. O pergaminho nunca muda.

Voce recebera `Q` consultas. Cada consulta informa `L` e `R`. Para cada consulta, responda:

```text
max(A[L..R]) - min(A[L..R]) + gcd(A[L..R])
```

Onde `gcd(A[L..R])` e o maximo divisor comum de todos os numeros do intervalo.

## Entrada

A primeira linha contem `N` e `Q`.

A segunda linha contem `N` inteiros `A_i`.

As proximas `Q` linhas contem `L` e `R`.

## Saida

Para cada consulta, imprima o valor pedido.

## Restricoes

```text
1 <= N, Q <= 300000
1 <= A_i <= 10^9
```

## Exemplo

Entrada:

```text
5 3
6 10 15 25 30
1 3
2 5
4 5
```

Saida:

```text
10
24
10
```

## Topicos Da Ementa

- `[P2]` Sparse Table;
- Range Minimum Query;
- algoritmo de Euclides;
- analise de complexidade.

## Dificuldade

Extremamente dificil.

## Ideia Esperada

Construir Sparse Tables separadas para:

- minimo;
- maximo;
- gcd.

Responder cada consulta em `O(1)` ou `O(log N)`, dependendo da abordagem do `gcd`.

---

# 3. Cofres Complementares

Existem `N` cristais, cada um com valor `A_i`. Um cofre abre se for escolhido um subconjunto de cristais cuja soma seja exatamente `S`.

Determine quantos subconjuntos abrem o cofre.

## Entrada

A primeira linha contem `N` e `S`.

A segunda linha contem `N` inteiros `A_i`.

## Saida

Imprima a quantidade de subconjuntos cuja soma e `S`.

## Restricoes

```text
1 <= N <= 44
0 <= S <= 10^18
0 <= A_i <= 10^18
```

## Exemplo

Entrada:

```text
5 10
2 3 5 7 8
```

Saida:

```text
3
```

## Explicacao

Subconjuntos com soma `10`:

```text
2 + 3 + 5
2 + 8
3 + 7
```

## Topicos Da Ementa

- `[P2]` Meet-in-the-Middle;
- argumentos de contagem;
- forca bruta otimizada;
- dicionario/mapa de frequencias.

## Dificuldade

Extremamente dificil.

## Ideia Esperada

Dividir os `N` elementos em duas metades.

Gerar todas as somas da primeira metade e todas as somas da segunda metade.

Contar pares de somas que completam `S`.

---

# 4. Curso Critico

Uma universidade possui `N` disciplinas e `M` pre-requisitos. Cada disciplina `i` tem duracao `D_i`.

Se existe uma dependencia `A B`, entao a disciplina `A` deve ser concluida antes da disciplina `B`.

Determine o menor tempo necessario para concluir todas as disciplinas, assumindo que varias disciplinas podem ser cursadas em paralelo, desde que seus pre-requisitos tenham sido cumpridos.

Se houver ciclo de dependencias, imprima:

```text
IMPOSSIVEL
```

## Entrada

A primeira linha contem `N` e `M`.

A segunda linha contem `N` inteiros `D_i`.

As proximas `M` linhas contem `A` e `B`.

## Saida

Imprima o menor tempo total ou `IMPOSSIVEL`.

## Restricoes

```text
1 <= N, M <= 200000
1 <= D_i <= 10^9
```

## Exemplo

Entrada:

```text
5 4
3 2 4 6 1
1 3
2 3
3 4
3 5
```

Saida:

```text
13
```

## Topicos Da Ementa

- `[P2]` DP em grafos direcionados aciclicos;
- ordenacao topologica;
- algoritmo de Kahn;
- caminhos mais longos em DAG.

## Dificuldade

Extremamente dificil.

## Ideia Esperada

Fazer ordenacao topologica.

Para cada disciplina, calcular o maior tempo acumulado ate ela.

A resposta e o maior valor final.

---

# 5. Laboratorio Hamiltoniano

Um robo deve visitar `N` salas de um laboratorio, numeradas de `0` a `N - 1`.

Ele comeca na sala `0` e deve visitar cada sala exatamente uma vez.

Existe um custo `C[i][j]` para ir da sala `i` para a sala `j`.

Determine o menor custo para visitar todas as salas.

## Entrada

A primeira linha contem `N`.

Depois seguem `N` linhas, cada uma com `N` inteiros.

## Saida

Imprima o menor custo.

## Restricoes

```text
1 <= N <= 20
0 <= C[i][j] <= 10^9
```

## Exemplo

Entrada:

```text
4
0 10 15 20
10 0 35 25
15 35 0 30
20 25 30 0
```

Saida:

```text
50
```

## Topicos Da Ementa

- `[P2]` DP com mascara de bits;
- caminho Hamiltoniano;
- programacao dinamica;
- representacao binaria de subconjuntos.

## Dificuldade

Extremamente dificil.

## Ideia Esperada

Usar `dp[mask][u]`:

```text
menor custo para visitar o conjunto mask e terminar em u
```

---

# 6. Reinos Fortemente Conectados

Existem `N` reinos e `M` rotas direcionadas.

Dois reinos pertencem ao mesmo imperio se e possivel sair de um e chegar ao outro, e tambem voltar.

Depois de descobrir os imperios, construa o grafo condensado e determine quantos imperios nao recebem nenhuma rota de outro imperio.

## Entrada

A primeira linha contem `N` e `M`.

As proximas `M` linhas contem `A` e `B`, indicando uma rota de `A` para `B`.

## Saida

Imprima a quantidade de componentes fortemente conexas com grau de entrada zero no grafo condensado.

## Restricoes

```text
1 <= N, M <= 300000
```

## Exemplo

Entrada:

```text
5 5
1 2
2 1
2 3
3 4
4 3
```

Saida:

```text
2
```

## Topicos Da Ementa

- `[P2]` Componentes fortemente conexas;
- Kosaraju ou Tarjan;
- grafos direcionados;
- grafo condensado.

## Dificuldade

Extremamente dificil.

## Ideia Esperada

Encontrar SCCs.

Comprimir cada SCC em um no.

Contar quantas componentes nao possuem arestas chegando de outras componentes.

---

# 7. Pontes Da Capital

Uma rede de `N` cidades possui `M` estradas bidirecionais.

Uma estrada e critica se, ao remove-la, aumenta o numero de componentes conexas da rede.

Determine quantas estradas criticas existem.

## Entrada

A primeira linha contem `N` e `M`.

As proximas `M` linhas contem `A` e `B`.

## Saida

Imprima a quantidade de pontes.

## Restricoes

```text
1 <= N, M <= 300000
```

## Exemplo

Entrada:

```text
5 5
1 2
2 3
3 1
3 4
4 5
```

Saida:

```text
2
```

## Topicos Da Ementa

- `[P2]` DFS traversal tree;
- Tarjan para pontes;
- componentes conexas;
- low-link.

## Dificuldade

Extremamente dificil.

## Ideia Esperada

Usar DFS com:

```text
tin[v] = tempo de entrada
low[v] = menor tempo alcancavel
```

Uma aresta `v-u` e ponte se:

```text
low[u] > tin[v]
```

---

# 8. Biblioteca De Subarvores

Uma biblioteca digital e organizada como uma arvore enraizada no documento `1`.

Cada documento possui um tema representado por um inteiro.

Para cada documento `v`, determine quantos temas diferentes aparecem em sua subarvore.

## Entrada

A primeira linha contem `N`.

A segunda linha contem `N` inteiros, os temas.

As proximas `N - 1` linhas contem as arestas da arvore.

## Saida

Imprima `N` inteiros, onde o `i`-esimo valor e a resposta para o documento `i`.

## Restricoes

```text
1 <= N <= 300000
1 <= tema_i <= 10^9
```

## Exemplo

Entrada:

```text
5
1 2 1 3 2
1 2
1 3
2 4
2 5
```

Saida:

```text
3 2 1 1 1
```

## Topicos Da Ementa

- `[P2]` Small-to-Large;
- arvores enraizadas;
- subarvores;
- DFS.

## Dificuldade

Extremamente dificil.

## Ideia Esperada

Cada subarvore devolve um conjunto de temas.

Sempre unir o conjunto menor dentro do maior para reduzir custo total.

---

# 9. Trilhas E Ancestrais

Uma arvore possui `N` vertices. Cada aresta possui um peso.

Voce recebera `Q` consultas `u v`. Para cada consulta, determine o maior peso de uma aresta no caminho entre `u` e `v`.

## Entrada

A primeira linha contem `N` e `Q`.

As proximas `N - 1` linhas contem `A`, `B` e `W`.

As proximas `Q` linhas contem `u` e `v`.

## Saida

Para cada consulta, imprima o maior peso no caminho.

## Restricoes

```text
1 <= N, Q <= 300000
1 <= W <= 10^9
```

## Exemplo

Entrada:

```text
5 3
1 2 4
1 3 2
2 4 7
2 5 1
4 5
4 3
5 3
```

Saida:

```text
7
7
4
```

## Topicos Da Ementa

- `[P2]` Binary Lifting;
- LCA;
- arvores;
- consultas em caminho.

## Dificuldade

Extremamente dificil.

## Ideia Esperada

Durante o Binary Lifting, guardar tambem o maior peso ao subir `2^k` ancestrais.

---

# 10. Fronteira Do Campus

Um campus universitario possui `N` pontos de referencia no plano.

O setor de engenharia deseja cercar todos os pontos com a menor cerca convexa possivel.

Determine:

1. quantos pontos ficam na fronteira da cerca;
2. o dobro da area da cerca.

Pontos colineares na borda devem ser contados como pontos de fronteira.

## Entrada

A primeira linha contem `N`.

As proximas `N` linhas contem `x` e `y`.

## Saida

Imprima dois valores:

```text
quantidade_de_pontos_na_borda dobro_da_area
```

## Restricoes

```text
1 <= N <= 300000
-10^9 <= x, y <= 10^9
```

## Exemplo

Entrada:

```text
5
0 0
2 0
2 2
0 2
1 1
```

Saida:

```text
4 8
```

## Topicos Da Ementa

- `[P2]` Convex Hull;
- produto vetorial;
- area de poligono;
- formula do cadarco;
- geometria computacional.

## Dificuldade

Extremamente dificil.

## Ideia Esperada

Construir o fecho convexo com monotonic chain.

Depois calcular o dobro da area usando a formula do cadarco.

---

# Mapa Da Ementa Por Problema

| Problema | Topicos principais |
|---:|---|
| 1 | Segment Tree, Lazy Propagation |
| 2 | Sparse Table, RMQ, GCD |
| 3 | Meet-in-the-Middle, contagem |
| 4 | DP em DAG, ordenacao topologica |
| 5 | DP com mascara de bits |
| 6 | SCC, Kosaraju/Tarjan, grafo condensado |
| 7 | Tarjan, pontes, DFS tree |
| 8 | Small-to-Large, subarvores |
| 9 | Binary Lifting, LCA, consultas em caminho |
| 10 | Convex Hull, produto vetorial, area de poligono |

---

# Nivel De Prioridade Para Treino

Se houver pouco tempo, treinar nesta ordem:

1. Problema 4 - Curso Critico;
2. Problema 3 - Cofres Complementares;
3. Problema 6 - Reinos Fortemente Conectados;
4. Problema 9 - Trilhas E Ancestrais;
5. Problema 1 - Arquivos Com Versoes.

Esses cinco problemas cobrem uma parte forte da ementa universitaria e obrigam o aluno a pensar em modelagem, estrutura e complexidade.

