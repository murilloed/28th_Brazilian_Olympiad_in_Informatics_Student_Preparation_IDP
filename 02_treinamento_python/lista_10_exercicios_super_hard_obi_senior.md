# Lista De 10 Exercicios Super Hard - OBI Nivel Senior

Esta lista foi criada para treino avancado de alunos que ja dominam entrada/saida, listas, dicionarios, conjuntos, BFS/DFS, ordenacao, busca binaria e programacao dinamica basica.

Os problemas abaixo exigem combinar tecnicas e pensar em complexidade.

## Orientacoes

Para cada exercicio, entregar:

- ideia da solucao;
- estrutura de dados usada;
- complexidade;
- codigo em Python;
- pelo menos 3 testes proprios.

---

# 1. Arquivo Vivo

Um arquivo possui `N` posicoes numeradas de `1` a `N`. Inicialmente, a posicao `i` possui valor `A_i`.

Voce deve processar `Q` operacoes:

- `1 L R X`: somar `X` em todas as posicoes de `L` a `R`;
- `2 L R`: imprimir a soma dos valores de `L` a `R`.

## Entrada

A primeira linha contem `N` e `Q`.

A segunda linha contem `N` inteiros `A_i`.

As proximas `Q` linhas contem as operacoes.

## Saida

Para cada operacao do tipo `2`, imprima a soma pedida.

## Restricoes

```text
1 <= N, Q <= 200000
0 <= A_i <= 10^9
0 <= X <= 10^9
```

## Exemplo

Entrada:

```text
5 4
1 2 3 4 5
2 1 5
1 2 4 10
2 1 5
2 3 3
```

Saida:

```text
15
45
13
```

## Tema Esperado

Segment Tree com Lazy Propagation.

## Por Que E Super Hard?

Atualizar intervalo elemento por elemento custa `O(NQ)`, que e inviavel.

---

# 2. Minimo E Maximo Da Jornada

Voce recebe um vetor fixo `A` com `N` valores e `Q` consultas.

Cada consulta informa `L` e `R`. Para cada consulta, imprima:

```text
max(A[L..R]) - min(A[L..R])
```

O vetor nunca muda.

## Entrada

A primeira linha contem `N` e `Q`.

A segunda linha contem `N` inteiros.

As proximas `Q` linhas contem `L` e `R`.

## Saida

Para cada consulta, imprima a diferenca entre maximo e minimo no intervalo.

## Restricoes

```text
1 <= N, Q <= 300000
1 <= A_i <= 10^9
```

## Exemplo

Entrada:

```text
6 3
8 2 5 1 9 3
1 6
2 4
3 5
```

Saida:

```text
8
4
8
```

## Tema Esperado

Sparse Table para minimo e maximo.

## Por Que E Super Hard?

Consultar intervalo com loop custa muito. Como o vetor e fixo, pre-processamento resolve.

---

# 3. Subconjunto Exato

Voce recebe `N` numeros e um alvo `S`.

Conte quantos subconjuntos possuem soma exatamente `S`.

## Entrada

A primeira linha contem `N` e `S`.

A segunda linha contem `N` inteiros.

## Saida

Imprima a quantidade de subconjuntos com soma `S`.

## Restricoes

```text
1 <= N <= 40
0 <= S <= 10^15
0 <= A_i <= 10^15
```

## Exemplo

Entrada:

```text
4 10
2 3 5 7
```

Saida:

```text
2
```

## Explicacao

Subconjuntos:

```text
3 + 7 = 10
2 + 3 + 5 = 10
```

## Tema Esperado

Meet-in-the-Middle.

## Por Que E Super Hard?

`2^40` e impossivel, mas `2^20 + 2^20` e viavel.

---

# 4. Rotas Com Pedagio Negativo

Um reino possui `N` cidades e `M` estradas direcionadas. Cada estrada possui custo, que pode ser negativo.

Determine a menor distancia da cidade `1` para todas as outras.

Se existir um ciclo negativo alcancavel a partir da cidade `1`, imprima:

```text
CICLO NEGATIVO
```

## Entrada

A primeira linha contem `N` e `M`.

As proximas `M` linhas contem `A`, `B` e `C`, indicando uma estrada de `A` para `B` com custo `C`.

## Saida

Se houver ciclo negativo alcancavel, imprima `CICLO NEGATIVO`.

Caso contrario, imprima as menores distancias, usando `INF` para cidades inalcançaveis.

## Restricoes

```text
1 <= N <= 5000
0 <= M <= 30000
-10^9 <= C <= 10^9
```

## Exemplo

Entrada:

```text
4 4
1 2 3
2 3 -5
3 2 1
3 4 2
```

Saida:

```text
CICLO NEGATIVO
```

## Tema Esperado

Bellman-Ford com deteccao de ciclo negativo.

## Por Que E Super Hard?

Dijkstra nao funciona com pesos negativos.

---

# 5. Grupos Secretos

Em uma rede com `N` bases e `M` mensagens direcionadas, duas bases pertencem ao mesmo grupo secreto se uma consegue enviar mensagem para a outra e receber de volta por algum caminho.

Para cada base, imprima o identificador do seu grupo secreto.

Os grupos devem ser numerados na ordem em que forem descobertos.

## Entrada

A primeira linha contem `N` e `M`.

As proximas `M` linhas contem `A` e `B`, indicando mensagem de `A` para `B`.

## Saida

Imprima `N` inteiros, onde o `i`-esimo inteiro e o grupo da base `i`.

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
1 1 2 2 3
```

## Tema Esperado

Componentes fortemente conexas: Kosaraju ou Tarjan.

## Por Que E Super Hard?

Grafo direcionado exige ida e volta, nao apenas conexao simples.

---

# 6. Ancestrais Do Reino

Um reino e representado por uma arvore enraizada no vertice `1`.

Voce recebera `Q` consultas:

```text
u v
```

Para cada consulta, imprima o ancestral comum mais profundo de `u` e `v`.

## Entrada

A primeira linha contem `N` e `Q`.

As proximas `N - 1` linhas contem as arestas da arvore.

As proximas `Q` linhas contem as consultas.

## Saida

Para cada consulta, imprima o LCA de `u` e `v`.

## Restricoes

```text
1 <= N, Q <= 300000
```

## Exemplo

Entrada:

```text
5 3
1 2
1 3
2 4
2 5
4 5
4 3
2 3
```

Saida:

```text
2
1
1
```

## Tema Esperado

Binary Lifting, LCA.

## Por Que E Super Hard?

Subir pai por pai em cada consulta pode virar `O(NQ)`.

---

# 7. Cores Das Subarvores

Uma arvore possui `N` vertices. Cada vertice tem uma cor.

Para cada vertice `v`, determine quantas cores diferentes aparecem na subarvore de `v`, considerando a arvore enraizada em `1`.

## Entrada

A primeira linha contem `N`.

A segunda linha contem `N` inteiros, as cores dos vertices.

As proximas `N - 1` linhas contem as arestas.

## Saida

Imprima `N` inteiros: a resposta para cada vertice.

## Restricoes

```text
1 <= N <= 200000
1 <= cor_i <= 10^9
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

## Tema Esperado

DFS em arvore, Small-to-Large ou Euler Tour com estruturas de frequencia.

## Por Que E Super Hard?

Juntar conjuntos de todas as subarvores ingenuamente pode custar `O(N^2)`.

---

# 8. Entregas Com Mascara

Existem `N` cidades, numeradas de `0` a `N - 1`, com `N <= 20`.

Um entregador começa na cidade `0` e quer visitar todas as cidades exatamente uma vez, minimizando o custo total.

Voce recebe uma matriz de custos `C`, onde `C[i][j]` e o custo de ir de `i` para `j`.

## Entrada

A primeira linha contem `N`.

Depois seguem `N` linhas com `N` inteiros.

## Saida

Imprima o menor custo para sair de `0` e visitar todas as cidades.

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

## Tema Esperado

DP com mascara de bits.

## Por Que E Super Hard?

O estado precisa guardar quais cidades ja foram visitadas e onde o entregador esta.

---

# 9. Ponto Dentro Da Fortaleza

Uma fortaleza e representada por um poligono simples com `N` vertices em ordem.

Depois, `Q` pontos sao consultados. Para cada ponto, diga se ele esta dentro da fortaleza.

Pontos exatamente na borda devem ser considerados dentro.

## Entrada

A primeira linha contem `N` e `Q`.

As proximas `N` linhas contem os vertices do poligono.

As proximas `Q` linhas contem os pontos consultados.

## Saida

Para cada ponto, imprima:

```text
DENTRO
```

ou:

```text
FORA
```

## Restricoes

```text
3 <= N <= 200000
1 <= Q <= 200000
-10^9 <= x, y <= 10^9
```

## Exemplo

Entrada:

```text
4 3
0 0
4 0
4 4
0 4
2 2
4 2
5 5
```

Saida:

```text
DENTRO
DENTRO
FORA
```

## Tema Esperado

Geometria computacional, produto vetorial, ponto em poligono.

## Por Que E Super Hard?

E preciso tratar borda, colinearidade e muitas consultas.

---

# 10. Muralha Externa

Um conjunto possui `N` pontos no plano. Determine o perimetro da menor muralha convexa que envolve todos os pontos.

Imprima o resultado com exatamente 6 casas decimais.

## Entrada

A primeira linha contem `N`.

As proximas `N` linhas contem `x` e `y`.

## Saida

Imprima o perimetro do fecho convexo.

## Restricoes

```text
1 <= N <= 200000
-10^9 <= x, y <= 10^9
```

## Exemplo

Entrada:

```text
4
0 0
0 1
1 0
1 1
```

Saida:

```text
4.000000
```

## Tema Esperado

Convex Hull, ordenacao, produto vetorial, distancia euclidiana.

## Por Que E Super Hard?

Exige geometria, ordenacao correta e cuidado com pontos colineares.

---

# Mapa De Tecnicas

| Questao | Tecnica principal |
|---:|---|
| 1 | Segment Tree + Lazy |
| 2 | Sparse Table |
| 3 | Meet-in-the-Middle |
| 4 | Bellman-Ford |
| 5 | SCC |
| 6 | LCA / Binary Lifting |
| 7 | Small-to-Large |
| 8 | DP com bitmask |
| 9 | Ponto em poligono |
| 10 | Convex Hull |

