# Ementa OBI 2026 - Modalidade Programacao Nivel 2 (P2) Com Foco Em Python

Este documento resume os itens da ementa da OBI que interessam aos alunos do Nivel 2 (P2).  
Como a regra da ementa e cumulativa, a turma P2 pode encontrar:

- topicos marcados como `[PM]`;
- topicos marcados como `[PJ]`;
- topicos marcados como `[P1]`;
- topicos marcados como `[P2]`.

Os itens `[P2]` sao os mais avancados e exclusivos do Nivel 2 e do Nivel Senior.  
Os itens anteriores aparecem como base obrigatoria para resolver problemas mais dificeis.

## Como Ler Esta Ementa

Para a turma, o objetivo nao e decorar nomes de algoritmos. O objetivo e reconhecer o tipo de problema e saber qual tecnica tentar em Python.

Em Python, os alunos devem se preparar para:

- ler entrada rapidamente com `input()` e `sys.stdin`;
- usar listas, matrizes, dicionarios e conjuntos;
- implementar buscas, ordenacoes e simulacoes;
- representar grafos com listas de adjacencia;
- usar `deque`, `heapq`, `set`, `dict` e listas de frequencia;
- entender complexidade para nao escolher uma solucao lenta;
- testar exemplos pequenos antes de submeter.

---

# 1. Fundamentos De Matematica

## 1.1 Aritmetica E Geometria

Pode cair para P2:

- numeros inteiros, operacoes e comparacoes;
- sinal, paridade e divisibilidade;
- numeros primos;
- fracoes e porcentagens;
- coordenadas no plano;
- distancia euclidiana;
- Teorema de Pitagoras;
- aritmetica modular basica;
- poligonos, vertices, lados, convexidade e area.

O que aprender em Python:

- usar `+`, `-`, `*`, `/`, `//`, `%` e `**`;
- diferenciar divisao real `/` de divisao inteira `//`;
- usar modulo `%` para paridade, divisibilidade e ciclos;
- calcular distancias com diferencas de coordenadas;
- evitar `float` quando o problema puder ser resolvido com inteiros.

Exemplo:

```python
x = int(input())

if x % 2 == 0:
    print("PAR")
else:
    print("IMPAR")
```

## 1.2 Logica

Pode cair para P2:

- proposicoes verdadeiras e falsas;
- conectivos `e`, `ou`, `nao`;
- implicacao;
- tabelas-verdade;
- provas diretas, contradicao e contrapositiva;
- inducao matematica.

O que aprender em Python:

- usar `and`, `or` e `not`;
- montar condicionais corretas;
- transformar regras do enunciado em expressoes logicas;
- testar todos os casos de uma condicao.

Exemplo:

```python
idade, nota = map(int, input().split())

if idade <= 20 and nota >= 60:
    print("APTO")
else:
    print("NAO APTO")
```

## 1.3 Matematica Discreta

Pode cair para P2:

- funcoes e relacoes;
- ordem lexicografica;
- conjuntos;
- recursao;
- permutacoes e fatorial;
- progressao aritmetica;
- principio da casa dos pombos;
- principio aditivo e multiplicativo;
- teoria dos jogos basica;
- progressao geometrica;
- combinacoes;
- triangulo de Pascal;
- inclusao-exclusao.

O que aprender em Python:

- usar `set` para conjuntos;
- usar `sorted()` para ordem lexicografica;
- implementar fatorial e combinacoes;
- usar recursao com cuidado;
- reconhecer problemas de contagem.

Exemplo:

```python
a = set(map(int, input().split()))
b = set(map(int, input().split()))

print(len(a & b))
```

## 1.4 Grafos - Conceitos Matematicos

Pode cair para P2:

- grafos nao direcionados;
- grafos direcionados;
- vertices, arestas, grau, adjacencia;
- caminhos e ciclos;
- componentes conexas;
- arvores e florestas;
- arvores enraizadas.

O que aprender em Python:

- representar grafo com lista de adjacencia;
- usar DFS e BFS;
- diferenciar grafo direcionado e nao direcionado;
- entender grau de entrada e saida.

Exemplo:

```python
n, m = map(int, input().split())
g = [[] for _ in range(n)]

for _ in range(m):
    a, b = map(int, input().split())
    g[a].append(b)
    g[b].append(a)
```

---

# 2. Fundamentos De Computacao

## 2.1 Informatica Basica

Pode cair indiretamente:

- uso de computador;
- sistema operacional;
- editor de codigo;
- navegador;
- organizacao de arquivos.

O que aprender em Python:

- criar e salvar arquivos `.py`;
- executar codigo no ambiente de prova;
- copiar e testar entradas;
- interpretar mensagens de erro simples.

## 2.2 Programacao

Pode cair para P2:

- variaveis;
- expressoes;
- tipos primitivos;
- operadores aritmeticos;
- entrada e saida padrao;
- condicionais;
- repeticoes;
- operadores logicos;
- strings;
- vetores e matrizes;
- funcoes;
- recursao;
- memoria, pilha de recursao e referencias;
- representacao binaria;
- operadores de bits.

O que aprender em Python:

- `int`, `float`, `bool`, `str`;
- `list` para vetores;
- lista de listas para matrizes;
- `def` para funcoes;
- `sys.setrecursionlimit()` quando usar DFS recursiva;
- operadores de bits: `&`, `|`, `^`, `~`, `<<`, `>>`.

Exemplo:

```python
def eh_par(x):
    return x % 2 == 0

n = int(input())
print("SIM" if eh_par(n) else "NAO")
```

---

# 3. Analise De Algoritmos

Pode cair para P2:

- conceito de algoritmo;
- corretude;
- eficiencia;
- pre-condicao e pos-condicao;
- Big O;
- complexidade constante, logaritmica, linear, quadratica, cubica, exponencial e fatorial;
- trade-off espaco-tempo;
- desempenho empirico.

O que aprender em Python:

- estimar se uma solucao passa pelo limite do enunciado;
- evitar O(n²) quando `n` for grande;
- saber quando usar ordenacao, busca binaria, dicionario ou prefixo;
- entender que Python e pratico, mas pode ser lento se o algoritmo for ruim.

Exemplo:

```python
# O(n)
n = int(input())
v = list(map(int, input().split()))
print(max(v))
```

---

# 4. Estrategias De Algoritmos

Pode cair para P2:

- iteracao e repeticao;
- forca bruta;
- algoritmos gulosos;
- backtracking;
- divisao e conquista;
- programacao dinamica.

O que aprender em Python:

- testar todas as possibilidades quando os limites forem pequenos;
- usar guloso quando uma escolha local pode ser justificada;
- usar backtracking com poda;
- dividir problemas em partes menores;
- usar DP quando existem subproblemas repetidos.

Exemplo de guloso:

```python
n = int(input())
moedas = [100, 50, 25, 10, 5, 1]
qtd = 0

for moeda in moedas:
    qtd += n // moeda
    n %= moeda

print(qtd)
```

---

# 5. Estruturas De Dados

## 5.1 Estruturas Basicas E Intermediarias

Pode cair para P2:

- histograma ou vetor de frequencias;
- somas parciais;
- prefixos e sufixos;
- conjunto `set`;
- dicionario `dict`;
- fila de prioridades `heapq`;
- pilha;
- fila;
- representacoes de grafos;
- Union-Find;
- Fenwick Tree.

O que aprender em Python:

- `list` para vetor;
- `dict` para contagem por chave;
- `set` para existencia sem repeticao;
- `deque` para fila;
- `heapq` para menor prioridade;
- listas de adjacencia para grafos;
- implementar Union-Find;
- implementar Fenwick para soma prefixada dinamica.

Exemplo com frequencia:

```python
from collections import Counter

v = list(map(int, input().split()))
freq = Counter(v)
print(freq.most_common(1)[0][0])
```

## 5.2 Estruturas Exclusivas P2

Topicos `[P2]`:

- Sparse Table;
- Range Minimum Query;
- Segment Tree;
- Lazy Propagation.

O que aprender em Python:

- usar Sparse Table quando o vetor nao muda e ha muitas consultas de minimo/maximo;
- usar Segment Tree quando ha consultas e atualizacoes;
- usar Lazy Propagation quando a atualizacao e em intervalo.

Resumo pratico:

| Estrutura | Quando usar |
|---|---|
| Sparse Table | muitas consultas, vetor fixo |
| Segment Tree | consultas e atualizacoes |
| Lazy Propagation | atualizacoes em intervalo |

---

# 6. Ordenacao E Busca

Pode cair para P2:

- ordenacao com biblioteca;
- ordenacao por contagem;
- dois ponteiros;
- busca binaria;
- busca binaria na resposta;
- Merge Sort;
- Meet-in-the-Middle.

O que aprender em Python:

- `sort()` e `sorted()`;
- `bisect_left` e `bisect_right`;
- implementar dois ponteiros;
- reconhecer problemas de "menor valor que satisfaz";
- entender Merge Sort para contagem de inversoes;
- usar Meet-in-the-Middle para subconjuntos com `n` em torno de 40.

Exemplo de busca binaria:

```python
from bisect import bisect_left

v = list(map(int, input().split()))
x = int(input())
v.sort()

pos = bisect_left(v, x)
print(pos)
```

---

# 7. Algoritmos De Matematica

Pode cair para P2:

- conversao entre bases;
- MDC pelo algoritmo de Euclides;
- primalidade por divisao por tentativas;
- listar divisores;
- Crivo de Eratostenes;
- fatoracao;
- exponenciacao rapida.

O que aprender em Python:

- `math.gcd`;
- implementar crivo;
- testar primalidade ate raiz quadrada;
- usar exponenciacao modular com `pow(base, expoente, modulo)`.

Exemplo:

```python
import math

a, b = map(int, input().split())
print(math.gcd(a, b))
```

---

# 8. Programacao Dinamica

Pode cair para P2:

- mochila com e sem repeticoes;
- contagem com DP;
- DP em prefixos de vetores e matrizes;
- Kadane;
- maior subsequencia comum;
- distancia de edicao;
- DP para jogos;
- LIS;
- DP em DAG;
- DP em intervalos;
- DP com mascara de bits.

O que aprender em Python:

- criar vetor `dp`;
- criar matriz `dp`;
- definir claramente o estado;
- definir transicao;
- definir caso base;
- tomar cuidado com memoria;
- usar bitmask quando `n` for pequeno.

Exemplo simples:

```python
n = int(input())
dp = [0] * (n + 1)
dp[0] = 1

for i in range(1, n + 1):
    dp[i] = dp[i - 1]
    if i >= 2:
        dp[i] += dp[i - 2]

print(dp[n])
```

---

# 9. Grafos

Pode cair para P2:

- DFS;
- BFS;
- componentes conexas;
- biparticao;
- flood fill;
- Dijkstra;
- Prim e Kruskal;
- ordenacao topologica;
- Bellman-Ford;
- Floyd-Warshall;
- caminho e ciclo de Euler;
- pontes e pontos de articulacao;
- componentes fortemente conexas.

O que aprender em Python:

- `deque` para BFS;
- recursao ou pilha para DFS;
- `heapq` para Dijkstra;
- Union-Find para Kruskal;
- grau de entrada para Kahn;
- Kosaraju ou Tarjan para SCC;
- Tarjan para pontes e articulacoes.

Exemplo de BFS:

```python
from collections import deque

n, m, inicio = map(int, input().split())
g = [[] for _ in range(n)]

for _ in range(m):
    a, b = map(int, input().split())
    g[a].append(b)
    g[b].append(a)

dist = [-1] * n
dist[inicio] = 0
fila = deque([inicio])

while fila:
    v = fila.popleft()
    for u in g[v]:
        if dist[u] == -1:
            dist[u] = dist[v] + 1
            fila.append(u)

print(*dist)
```

---

# 10. Arvores

Pode cair para P2:

- subarvores em arvores enraizadas;
- diametro e centro de arvore;
- grafos funcionais;
- Binary Lifting;
- LCA;
- pre-ordem, em-ordem, pos-ordem;
- Euler Tour;
- DP em arvores;
- Tree Rerooting;
- Small-to-Large.

O que aprender em Python:

- representar arvore como lista de adjacencia;
- fazer DFS com pai;
- calcular profundidade;
- calcular tamanho de subarvore;
- usar Euler Tour para transformar subarvore em intervalo;
- estudar LCA com Binary Lifting.

Exemplo de tamanho de subarvore:

```python
import sys
sys.setrecursionlimit(10**7)

n = int(input())
g = [[] for _ in range(n)]

for _ in range(n - 1):
    a, b = map(int, input().split())
    g[a].append(b)
    g[b].append(a)

tam = [0] * n

def dfs(v, p):
    tam[v] = 1
    for u in g[v]:
        if u != p:
            dfs(u, v)
            tam[v] += tam[u]

dfs(0, -1)
print(*tam)
```

---

# 11. Geometria

Topicos `[P2]`:

- vetores, retas e segmentos;
- compressao de coordenadas;
- produto escalar;
- produto vetorial;
- colinearidade;
- paralelismo;
- ortogonalidade;
- sentido do angulo;
- intersecao de retas;
- line sweep;
- radial sweep;
- convex hull;
- area de poligono;
- ponto em poligono.

O que aprender em Python:

- representar ponto como tupla `(x, y)`;
- calcular vetor entre dois pontos;
- usar produto vetorial para giro e colinearidade;
- usar formula do cadarco para area;
- usar compressao de coordenadas com `sorted(set(...))`;
- entender convex hull como "casca" externa dos pontos.

Exemplo de produto vetorial:

```python
def cross(a, b, c):
    return (b[0] - a[0]) * (c[1] - a[1]) - (b[1] - a[1]) * (c[0] - a[0])

ax, ay, bx, by, cx, cy = map(int, input().split())

valor = cross((ax, ay), (bx, by), (cx, cy))

if valor == 0:
    print("COLINEARES")
elif valor > 0:
    print("ESQUERDA")
else:
    print("DIREITA")
```

---

# Prioridade De Estudo Para A Turma P2

Como o tempo e curto, a prioridade deve ser:

## Prioridade 1 - Obrigatorio

- entrada e saida;
- listas e strings;
- ordenacao;
- busca binaria;
- dicionario e conjunto;
- prefix sum;
- BFS e DFS;
- representacao de grafos;
- complexidade Big O.

## Prioridade 2 - Muito Importante

- Dijkstra;
- Union-Find;
- topological sort;
- programacao dinamica basica;
- mochila;
- LIS;
- crivo;
- MDC;
- exponenciacao rapida.

## Prioridade 3 - P2 Avancado

- Sparse Table;
- Segment Tree;
- Meet-in-the-Middle;
- DP em DAG;
- DP em intervalos;
- DP com bitmask;
- Bellman-Ford;
- Floyd-Warshall;
- SCC;
- pontes;
- LCA;
- geometria computacional.

## Frase Para Os Alunos

> Para P2, Python e ferramenta. A nota vem de interpretar o problema, escolher uma tecnica adequada, implementar com cuidado e testar bem.

