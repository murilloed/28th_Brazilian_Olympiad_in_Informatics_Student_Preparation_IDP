# Lista De 20 Questoes Difíceis - Modelo OBI Nivel Senior

Esta lista foi criada para treino de alunos em **Programacao - Nivel Senior**, com enunciados originais inspirados no estilo das provas da OBI: narrativa curta, entrada/saida objetiva, restricoes grandes, subtarefas e necessidade de escolher boas estruturas/algoritmos.

## Orientacoes Para Os Alunos

- Leiam a entrada e a saida antes de pensar no codigo.
- Observem os limites: eles indicam a complexidade esperada.
- Tentem primeiro uma solucao simples para ganhar pontos parciais.
- Depois melhorem para passar nas restricoes maiores.
- Nao imprimam texto extra.

---

# 1. Fotos Do Festival

Em uma avenida existem `N` posicoes. Algumas posicoes possuem uma decoracao especial, marcada por `1`, e as demais sao marcadas por `0`.

Uma foto e considerada bonita se escolher um intervalo continuo da avenida que contenha **exatamente uma** decoracao especial.

Determine quantos intervalos bonitos existem.

## Entrada

A primeira linha contem `N`.

A segunda linha contem `N` inteiros `A_i`, cada um igual a `0` ou `1`.

## Saida

Imprima um inteiro: a quantidade de intervalos com exatamente um `1`.

## Restricoes

```text
1 <= N <= 200000
0 <= A_i <= 1
```

## Exemplo

Entrada:

```text
5
1 0 0 1 0
```

Saida:

```text
9
```

## Tema Esperado

Sequencias, contagem por blocos de zeros, dois ponteiros.

---

# 2. Escada Restaurada

Uma escadaria tem `N` degraus. Alguns degraus possuem altura conhecida e outros foram destruidos.

Se a altura de um degrau e desconhecida, ela aparece como `-1`.

Uma escadaria e valida se a diferenca entre alturas consecutivas nunca passa de `1`.

Para cada posicao desconhecida, determine a maior altura possivel respeitando todas as alturas conhecidas.

Se nao for possivel restaurar a escadaria, imprima `IMPOSSIVEL`.

## Entrada

A primeira linha contem `N`.

A segunda linha contem `N` inteiros `A_i`.

## Saida

Imprima `N` inteiros com as maiores alturas possiveis, ou `IMPOSSIVEL`.

## Restricoes

```text
1 <= N <= 200000
-1 <= A_i <= 10^9
```

## Exemplo

Entrada:

```text
5
5 -1 -1 -1 6
```

Saida:

```text
5 6 7 7 6
```

## Tema Esperado

Passagem esquerda-direita, direita-esquerda, restricoes por distancia.

---

# 3. Pontes Antigas

Um arquipelago possui `N` ilhas e `M` conexoes. Cada conexao e de tipo `1` ou `2`.

Voce pode remover no maximo `K` conexoes do tipo `2`.

A rede final deve ser uma arvore, isto e, deve conectar todas as ilhas sem ciclos.

Determine se e possivel obter uma arvore removendo no maximo `K` conexoes do tipo `2`, sem remover conexoes do tipo `1`.

## Entrada

A primeira linha contem `N`, `M` e `K`.

As proximas `M` linhas contem `a`, `b` e `t`, indicando conexao entre `a` e `b` do tipo `t`.

## Saida

Imprima `S` se for possivel, ou `N` caso contrario.

## Restricoes

```text
1 <= N <= 100000
0 <= M <= 200000
0 <= K <= 200000
1 <= t <= 2
```

## Exemplo

Entrada:

```text
4 5 1
1 2 1
2 3 1
3 1 1
3 4 2
2 4 2
```

Saida:

```text
N
```

## Tema Esperado

Union-Find, ciclos, arvore geradora, Kruskal adaptado.

---

# 4. Harmonia De Sinais

Existem `N` sinais. Cada sinal tem valor `A_i` e resistencia `B_i`.

Voce pode zerar a resistencia de no maximo `K` sinais.

A pontuacao de um sinal escolhido e:

```text
A_i - B_i
```

Se a resistencia for zerada, a pontuacao vira:

```text
A_i
```

Escolha todos os sinais com pontuacao positiva depois das alteracoes. Qual a maior soma possivel?

## Entrada

A primeira linha contem `N` e `K`.

A segunda linha contem `N` inteiros `A_i`.

A terceira linha contem `N` inteiros `B_i`.

## Saida

Imprima a maior soma possivel.

## Restricoes

```text
1 <= N <= 200000
0 <= K <= N
1 <= A_i, B_i <= 10^9
```

## Exemplo

Entrada:

```text
5 2
4 10 2 8 7
5 3 6 10 1
```

Saida:

```text
25
```

## Tema Esperado

Guloso, ordenacao por ganho, escolha de melhores melhorias.

---

# 5. Energia Entre Torres

Existem `N` torres alinhadas, cada uma com altura `A_i`.

A energia entre duas torres `i` e `j` e:

```text
|i - j| + |A_i - A_j|
```

Determine a maior energia entre quaisquer duas torres.

## Entrada

A primeira linha contem `N`.

A segunda linha contem `N` inteiros `A_i`.

## Saida

Imprima a maior energia.

## Restricoes

```text
2 <= N <= 200000
1 <= A_i <= 10^9
```

## Exemplo

Entrada:

```text
5
3 10 4 8 1
```

Saida:

```text
11
```

## Tema Esperado

Manipulacao de modulo, maximos de expressoes, transformacao matematica.

---

# 6. Consultas De Energia

Existem `N` torres com alturas `A_i`.

Voce recebera `Q` consultas. Cada consulta informa `L` e `R`. Para cada consulta, determine a maior energia entre duas torres dentro do intervalo `[L, R]`.

Energia:

```text
|i - j| + |A_i - A_j|
```

## Entrada

A primeira linha contem `N` e `Q`.

A segunda linha contem `N` inteiros `A_i`.

As proximas `Q` linhas contem `L` e `R`.

## Saida

Para cada consulta, imprima a resposta.

## Restricoes

```text
2 <= N <= 100000
1 <= Q <= 100000
1 <= L < R <= N
```

## Exemplo

Entrada:

```text
5 2
3 10 4 8 1
1 5
2 4
```

Saida:

```text
11
8
```

## Tema Esperado

Sparse Table ou Segment Tree para maximo/minimo de transformacoes.

---

# 7. Mapa De Trilhas

Um mapa possui `N` cidades e `M` estradas bidirecionais. Cada estrada tem custo.

Determine o custo total minimo para conectar todas as cidades.

Se nao for possivel conectar todas, imprima `IMPOSSIVEL`.

## Entrada

A primeira linha contem `N` e `M`.

As proximas `M` linhas contem `a`, `b` e `c`.

## Saida

Imprima o custo da arvore geradora minima ou `IMPOSSIVEL`.

## Restricoes

```text
1 <= N <= 100000
0 <= M <= 200000
1 <= c <= 10^9
```

## Exemplo

Entrada:

```text
4 5
1 2 3
2 3 4
3 4 5
1 4 20
2 4 6
```

Saida:

```text
12
```

## Tema Esperado

Kruskal, Union-Find, arvore geradora minima.

---

# 8. Rotas Com Desconto

Existem `N` cidades e `M` estradas direcionadas. Cada estrada tem custo, que pode ser negativo por causa de descontos.

Determine o menor custo da cidade `1` ate todas as outras.

Se uma cidade for inalcançavel, imprima `INF`.

## Entrada

A primeira linha contem `N` e `M`.

As proximas `M` linhas contem `a`, `b` e `c`.

## Saida

Imprima `N` valores: as distancias a partir da cidade `1`.

## Restricoes

```text
1 <= N <= 5000
0 <= M <= 20000
-10^6 <= c <= 10^6
```

## Exemplo

Entrada:

```text
4 4
1 2 5
2 3 -2
1 3 10
3 4 1
```

Saida:

```text
0 5 3 4
```

## Tema Esperado

Bellman-Ford, relaxamento de arestas.

---

# 9. Ordem Das Tarefas

Uma competicao possui `N` tarefas. Algumas tarefas dependem de outras.

Se existe uma dependencia `a b`, a tarefa `a` deve ser feita antes de `b`.

Determine uma ordem valida para realizar todas as tarefas, ou imprima `IMPOSSIVEL` se houver ciclo.

## Entrada

A primeira linha contem `N` e `M`.

As proximas `M` linhas contem `a` e `b`.

## Saida

Imprima uma ordem valida ou `IMPOSSIVEL`.

## Restricoes

```text
1 <= N <= 200000
0 <= M <= 200000
```

## Exemplo

Entrada:

```text
4 3
1 2
1 3
3 4
```

Saida:

```text
1 2 3 4
```

## Tema Esperado

Ordenacao topologica, fila, grau de entrada.

---

# 10. Caminho Mais Longo Sem Ciclos

Dado um grafo direcionado aciclico com `N` vertices e `M` arestas, determine o tamanho do maior caminho.

## Entrada

A primeira linha contem `N` e `M`.

As proximas `M` linhas contem `a` e `b`, indicando uma aresta de `a` para `b`.

## Saida

Imprima o numero maximo de arestas em um caminho.

## Restricoes

```text
1 <= N <= 200000
0 <= M <= 200000
```

## Exemplo

Entrada:

```text
5 4
1 2
1 3
3 4
4 5
```

Saida:

```text
3
```

## Tema Esperado

DP em DAG, ordenacao topologica.

---

# 11. Senhas Possiveis

Uma senha tem tamanho `N`. Alguns caracteres ja sao conhecidos e outros aparecem como `?`.

Cada `?` pode ser substituido por qualquer letra minuscula de `a` a `z`.

Calcule quantas senhas diferentes podem ser formadas modulo `10^9 + 7`.

## Entrada

Uma string `S`.

## Saida

Imprima a quantidade de senhas possiveis modulo `10^9 + 7`.

## Restricoes

```text
1 <= |S| <= 1000000
```

## Exemplo

Entrada:

```text
a?b??
```

Saida:

```text
17576
```

## Tema Esperado

Exponenciacao rapida, combinatoria simples, modulo.

---

# 12. Escolha De Equipe

Ha `N` alunos e uma equipe deve ter exatamente `K` alunos.

Calcule quantas equipes diferentes podem ser formadas modulo `10^9 + 7`.

## Entrada

A primeira linha contem `N` e `K`.

## Saida

Imprima `C(N, K)` modulo `10^9 + 7`.

## Restricoes

```text
1 <= K <= N <= 1000000
```

## Exemplo

Entrada:

```text
5 2
```

Saida:

```text
10
```

## Tema Esperado

Fatorial modular, inverso modular, combinacoes.

---

# 13. Sequencia Crescente

Dada uma sequencia de `N` numeros, determine o tamanho da maior subsequencia crescente.

Uma subsequencia nao precisa ser continua.

## Entrada

A primeira linha contem `N`.

A segunda linha contem `N` inteiros.

## Saida

Imprima o tamanho da maior subsequencia crescente.

## Restricoes

```text
1 <= N <= 200000
1 <= A_i <= 10^9
```

## Exemplo

Entrada:

```text
6
5 1 4 2 3 10
```

Saida:

```text
4
```

## Tema Esperado

LIS em `O(N log N)`, busca binaria.

---

# 14. Moedas Raras

Voce tem `N` tipos de moedas. Cada tipo possui valor `V_i`. Voce pode usar cada moeda quantas vezes quiser.

Determine de quantas formas e possivel formar exatamente o valor `S`.

## Entrada

A primeira linha contem `N` e `S`.

A segunda linha contem `N` valores `V_i`.

## Saida

Imprima a quantidade de formas modulo `10^9 + 7`.

## Restricoes

```text
1 <= N <= 200
1 <= S <= 100000
1 <= V_i <= S
```

## Exemplo

Entrada:

```text
3 5
1 2 5
```

Saida:

```text
4
```

## Tema Esperado

Programacao dinamica, contagem, mochila com repeticao.

---

# 15. Submatriz Valiosa

Dada uma matriz `N x M` de inteiros, responda `Q` consultas.

Cada consulta informa `x1 y1 x2 y2`. Imprima a soma dos valores dentro desse retangulo.

## Entrada

A primeira linha contem `N`, `M` e `Q`.

Depois seguem `N` linhas com `M` inteiros.

Depois seguem `Q` consultas.

## Saida

Para cada consulta, imprima a soma.

## Restricoes

```text
1 <= N, M <= 1000
1 <= Q <= 200000
```

## Exemplo

Entrada:

```text
2 3 2
1 2 3
4 5 6
1 1 2 3
1 2 2 2
```

Saida:

```text
21
7
```

## Tema Esperado

Soma de prefixo 2D.

---

# 16. Guardas Na Muralha

Uma muralha tem `N` posicoes numeradas de `1` a `N`. Existem `M` intervalos vigiados por guardas.

Cada intervalo `[L, R]` indica que um guarda cobre todas as posicoes entre `L` e `R`.

Determine quantas posicoes sao cobertas por pelo menos um guarda.

## Entrada

A primeira linha contem `N` e `M`.

As proximas `M` linhas contem `L` e `R`.

## Saida

Imprima a quantidade de posicoes cobertas.

## Restricoes

```text
1 <= N <= 10^9
1 <= M <= 200000
```

## Exemplo

Entrada:

```text
10 3
1 4
3 6
8 9
```

Saida:

```text
8
```

## Tema Esperado

Ordenacao de intervalos, merge intervals, line sweep.

---

# 17. Labirinto De Cristal

Um labirinto e representado por uma matriz com `N` linhas e `M` colunas.

`.` indica celula livre e `#` indica parede.

Determine a menor quantidade de passos para sair de `S` e chegar em `T`.

## Entrada

A primeira linha contem `N` e `M`.

As proximas `N` linhas contem a matriz.

## Saida

Imprima a menor distancia, ou `-1` se nao houver caminho.

## Restricoes

```text
1 <= N, M <= 2000
```

## Exemplo

Entrada:

```text
3 4
S..#
##..
...T
```

Saida:

```text
5
```

## Tema Esperado

BFS em grid, fila, distancia minima.

---

# 18. Componentes Secretas

Em um grafo direcionado, duas bases pertencem ao mesmo grupo secreto se uma consegue chegar na outra e vice-versa.

Determine quantos grupos secretos existem.

## Entrada

A primeira linha contem `N` e `M`.

As proximas `M` linhas contem `a` e `b`, indicando uma aresta de `a` para `b`.

## Saida

Imprima a quantidade de componentes fortemente conexas.

## Restricoes

```text
1 <= N <= 200000
0 <= M <= 200000
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
3
```

## Tema Esperado

Kosaraju ou Tarjan, SCC.

---

# 19. Terreno Do Reino

Um terreno e representado por um poligono simples com `N` vertices em ordem.

Calcule o dobro da area do poligono.

## Entrada

A primeira linha contem `N`.

As proximas `N` linhas contem `x` e `y`.

## Saida

Imprima o dobro da area.

## Restricoes

```text
3 <= N <= 200000
-10^9 <= x, y <= 10^9
```

## Exemplo

Entrada:

```text
4
0 0
4 0
4 3
0 3
```

Saida:

```text
24
```

## Tema Esperado

Geometria, formula do cadarco, produto vetorial.

---

# 20. Muralha Convexa

Um reino possui `N` torres no plano. O rei deseja construir uma muralha reta por fora envolvendo todas as torres.

Determine quantas torres ficarao na borda da menor muralha convexa.

## Entrada

A primeira linha contem `N`.

As proximas `N` linhas contem `x` e `y`.

## Saida

Imprima a quantidade de pontos na borda do fecho convexo.

## Restricoes

```text
1 <= N <= 200000
-10^9 <= x, y <= 10^9
```

## Exemplo

Entrada:

```text
5
0 0
0 2
2 0
2 2
1 1
```

Saida:

```text
4
```

## Tema Esperado

Convex Hull, ordenacao, produto vetorial.

---

# Guia De Temas Por Questao

| Questao | Tema principal |
|---:|---|
| 1 | contagem em sequencia |
| 2 | reconstrucao com restricoes |
| 3 | Union-Find e ciclos |
| 4 | guloso e ordenacao |
| 5 | matematica com modulo absoluto |
| 6 | consultas em intervalo |
| 7 | Kruskal |
| 8 | Bellman-Ford |
| 9 | ordenacao topologica |
| 10 | DP em DAG |
| 11 | exponenciacao modular |
| 12 | combinatoria modular |
| 13 | LIS |
| 14 | DP de moedas |
| 15 | prefixo 2D |
| 16 | intervalos |
| 17 | BFS em grid |
| 18 | SCC |
| 19 | area de poligono |
| 20 | Convex Hull |

---

# Como Praticar

Sugestao de treino:

```text
Dia 1: Questoes 1 a 6
Dia 2: Questoes 7 a 13
Dia 3: Questoes 14 a 20
```

Para cada questao, entregar:

- ideia da solucao;
- complexidade esperada;
- codigo em Python;
- 3 testes proprios;
- explicacao do principal erro possivel.

