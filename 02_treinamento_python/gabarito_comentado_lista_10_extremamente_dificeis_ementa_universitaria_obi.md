# Gabarito Comentado - Lista De 10 Problemas Extremamente Dificeis

## Programacao Universitaria / OBI Nivel Senior

Este material apresenta uma solucao comentada para cada problema da lista **Lista De 10 Problemas Extremamente Dificeis**.

O objetivo nao e apenas mostrar o codigo final, mas explicar:

- qual e a ideia central;
- por que a solucao ingenua nao passa;
- qual estrutura de dados ou algoritmo resolve o problema;
- como pensar a solucao passo a passo;
- qual e a complexidade;
- uma implementacao de referencia em Python.

---

# 1. Arquivos Com Versoes

## Ideia Principal

O problema pede tres operacoes sobre intervalos:

- somar `X` em todos os elementos de `L` ate `R`;
- consultar o maior valor em `L..R`;
- consultar a soma dos valores em `L..R`.

Como `N` e `Q` podem chegar a `200000`, nao da para percorrer o intervalo inteiro em cada operacao. Se cada consulta custasse `O(N)`, o pior caso seria `O(N * Q)`, ou seja, ate `40 bilhoes` de passos.

A tecnica correta e usar uma **Segment Tree com Lazy Propagation**.

## Explicacao Para Leigo

Imagine que os arquivos estao em uma prateleira. Em vez de olhar arquivo por arquivo toda vez, criamos uma arvore de resumos.

Cada no da arvore guarda:

- a soma dos arquivos daquele pedaco;
- o maior valor daquele pedaco;
- uma atualizacao pendente, caso aquele pedaco inteiro tenha sido aumentado.

O lazy propagation serve para dizer:

> "Eu sei que todos os arquivos deste intervalo aumentaram, mas ainda nao preciso descer ate cada arquivo. Vou guardar essa informacao aqui e so aplicar nos filhos quando for necessario."

## Passo A Passo

1. Construir a arvore a partir do vetor inicial.
2. Em cada no, guardar:
   - `tree_sum`: soma do intervalo;
   - `tree_max`: maior valor do intervalo;
   - `lazy`: valor pendente para empurrar aos filhos.
3. Para atualizar um intervalo:
   - se o no esta totalmente dentro do intervalo, atualiza soma, maximo e lazy;
   - se esta parcialmente, desce para os filhos.
4. Para consultar:
   - se o no esta totalmente dentro, devolve o valor guardado;
   - se esta parcialmente, consulta os filhos e combina.

## Complexidade

```text
Construcao: O(N)
Atualizacao: O(log N)
Consulta: O(log N)
Memoria: O(N)
```

## Codigo Python

```python
import sys


class SegmentTree:
    def __init__(self, values):
        self.n = len(values)
        size = 4 * self.n
        self.sum_tree = [0] * size
        self.max_tree = [0] * size
        self.lazy = [0] * size
        self.values = values
        self.build(1, 0, self.n - 1)

    def build(self, node, left, right):
        if left == right:
            self.sum_tree[node] = self.values[left]
            self.max_tree[node] = self.values[left]
            return

        mid = (left + right) // 2
        self.build(node * 2, left, mid)
        self.build(node * 2 + 1, mid + 1, right)
        self.pull(node)

    def pull(self, node):
        self.sum_tree[node] = self.sum_tree[node * 2] + self.sum_tree[node * 2 + 1]
        self.max_tree[node] = max(self.max_tree[node * 2], self.max_tree[node * 2 + 1])

    def apply(self, node, left, right, value):
        self.sum_tree[node] += value * (right - left + 1)
        self.max_tree[node] += value
        self.lazy[node] += value

    def push(self, node, left, right):
        if self.lazy[node] == 0 or left == right:
            return

        mid = (left + right) // 2
        value = self.lazy[node]
        self.apply(node * 2, left, mid, value)
        self.apply(node * 2 + 1, mid + 1, right, value)
        self.lazy[node] = 0

    def update(self, ql, qr, value, node=1, left=0, right=None):
        if right is None:
            right = self.n - 1

        if qr < left or right < ql:
            return

        if ql <= left and right <= qr:
            self.apply(node, left, right, value)
            return

        self.push(node, left, right)
        mid = (left + right) // 2
        self.update(ql, qr, value, node * 2, left, mid)
        self.update(ql, qr, value, node * 2 + 1, mid + 1, right)
        self.pull(node)

    def query_sum(self, ql, qr, node=1, left=0, right=None):
        if right is None:
            right = self.n - 1

        if qr < left or right < ql:
            return 0

        if ql <= left and right <= qr:
            return self.sum_tree[node]

        self.push(node, left, right)
        mid = (left + right) // 2
        return (
            self.query_sum(ql, qr, node * 2, left, mid)
            + self.query_sum(ql, qr, node * 2 + 1, mid + 1, right)
        )

    def query_max(self, ql, qr, node=1, left=0, right=None):
        if right is None:
            right = self.n - 1

        if qr < left or right < ql:
            return -10**30

        if ql <= left and right <= qr:
            return self.max_tree[node]

        self.push(node, left, right)
        mid = (left + right) // 2
        return max(
            self.query_max(ql, qr, node * 2, left, mid),
            self.query_max(ql, qr, node * 2 + 1, mid + 1, right),
        )


def main():
    input = sys.stdin.readline
    n, q = map(int, input().split())
    values = list(map(int, input().split()))
    seg = SegmentTree(values)

    answers = []

    for _ in range(q):
        op = list(map(int, input().split()))

        if op[0] == 1:
            _, l, r, x = op
            seg.update(l - 1, r - 1, x)
        elif op[0] == 2:
            _, l, r = op
            answers.append(str(seg.query_max(l - 1, r - 1)))
        else:
            _, l, r = op
            answers.append(str(seg.query_sum(l - 1, r - 1)))

    print("\n".join(answers))


if __name__ == "__main__":
    main()
```

---

# 2. Pergaminhos E Consultas Imutaveis

## Ideia Principal

O vetor nunca muda. Isso permite fazer um pre-processamento caro uma vez e responder consultas rapidamente depois.

A estrutura ideal e a **Sparse Table**, muito usada para consultas em intervalos imutaveis.

Precisamos consultar:

- minimo no intervalo;
- maximo no intervalo;
- MDC no intervalo.

## Explicacao Para Leigo

Pense que voce quer responder perguntas sobre qualquer trecho de uma fila de numeros.

Em vez de calcular tudo do zero, voce guarda respostas para blocos de tamanho:

```text
1, 2, 4, 8, 16, 32, ...
```

Depois, qualquer intervalo pode ser respondido juntando dois blocos grandes.

## Passo A Passo

1. Criar tres Sparse Tables:
   - uma para minimo;
   - uma para maximo;
   - uma para MDC.
2. Para cada consulta `L R`:
   - calcular o tamanho do intervalo;
   - pegar `k = log2(tamanho)`;
   - combinar dois blocos de tamanho `2^k`;
   - calcular `maximo - minimo + mdc`.

## Complexidade

```text
Pre-processamento: O(N log N)
Consulta: O(1)
Memoria: O(N log N)
```

## Codigo Python

```python
import sys
from math import gcd


def build_sparse(values, func):
    n = len(values)
    log = (n).bit_length()
    table = [values[:]]

    length = 1
    for k in range(1, log):
        previous = table[k - 1]
        current = []

        for i in range(n - 2 * length + 1):
            current.append(func(previous[i], previous[i + length]))

        table.append(current)
        length *= 2

    return table


def query(table, left, right, func):
    length = right - left + 1
    k = length.bit_length() - 1
    block = 1 << k
    return func(table[k][left], table[k][right - block + 1])


def main():
    input = sys.stdin.readline
    n, q = map(int, input().split())
    values = list(map(int, input().split()))

    st_min = build_sparse(values, min)
    st_max = build_sparse(values, max)
    st_gcd = build_sparse(values, gcd)

    answers = []

    for _ in range(q):
        l, r = map(int, input().split())
        l -= 1
        r -= 1

        minimum = query(st_min, l, r, min)
        maximum = query(st_max, l, r, max)
        divisor = query(st_gcd, l, r, gcd)

        answers.append(str(maximum - minimum + divisor))

    print("\n".join(answers))


if __name__ == "__main__":
    main()
```

---

# 3. Cofres Complementares

## Ideia Principal

O problema pede contar subconjuntos com soma `S`.

Se `N = 44`, a forca bruta teria `2^44` subconjuntos, um numero inviavel.

A tecnica correta e **Meet-in-the-Middle**.

## Explicacao Para Leigo

Em vez de tentar todas as combinacoes dos 44 cristais de uma vez, dividimos em duas partes de 22.

Cada parte tem:

```text
2^22 combinacoes
```

Isso ainda e grande, mas e muito menor que `2^44`.

Depois procuramos pares:

```text
soma_da_primeira_metade + soma_da_segunda_metade = S
```

## Passo A Passo

1. Dividir o vetor em duas metades.
2. Gerar todas as somas possiveis da primeira metade.
3. Gerar todas as somas possiveis da segunda metade.
4. Contar quantas vezes cada soma aparece na segunda metade.
5. Para cada soma `x` da primeira metade, procurar `S - x`.

## Complexidade

```text
Tempo: O(2^(N/2))
Memoria: O(2^(N/2))
```

## Codigo Python

```python
import sys
from collections import Counter


def generate_sums(values):
    sums = [0]

    for value in values:
        new_sums = []
        for current in sums:
            new_sums.append(current + value)
        sums.extend(new_sums)

    return sums


def main():
    input = sys.stdin.readline
    n, target = map(int, input().split())
    values = list(map(int, input().split()))

    middle = n // 2
    left = values[:middle]
    right = values[middle:]

    left_sums = generate_sums(left)
    right_sums = generate_sums(right)

    frequency = Counter(right_sums)
    answer = 0

    for value in left_sums:
        answer += frequency[target - value]

    print(answer)


if __name__ == "__main__":
    main()
```

---

# 4. Curso Critico

## Ideia Principal

As disciplinas e pre-requisitos formam um grafo direcionado.

Se nao houver ciclo, temos um **DAG**. O tempo minimo para terminar tudo e o tamanho do caminho critico, isto e, o maior tempo acumulado considerando dependencias.

## Explicacao Para Leigo

Se uma disciplina depende de outra, ela so pode comecar depois.

Mas disciplinas independentes podem acontecer ao mesmo tempo.

Entao o tempo total nao e a soma de todas as duracoes. O tempo total e a maior cadeia de dependencias.

## Passo A Passo

1. Montar o grafo.
2. Calcular o grau de entrada de cada disciplina.
3. Comecar pelas disciplinas sem pre-requisito.
4. Fazer ordenacao topologica com fila.
5. Para cada disciplina, atualizar o melhor tempo para as disciplinas que dependem dela.
6. Se nem todos os vertices forem processados, existe ciclo.

## Complexidade

```text
Tempo: O(N + M)
Memoria: O(N + M)
```

## Codigo Python

```python
import sys
from collections import deque


def main():
    input = sys.stdin.readline
    n, m = map(int, input().split())
    duration = [0] + list(map(int, input().split()))

    graph = [[] for _ in range(n + 1)]
    indegree = [0] * (n + 1)

    for _ in range(m):
        a, b = map(int, input().split())
        graph[a].append(b)
        indegree[b] += 1

    queue = deque()
    finish_time = [0] * (n + 1)

    for node in range(1, n + 1):
        if indegree[node] == 0:
            queue.append(node)
            finish_time[node] = duration[node]

    processed = 0

    while queue:
        current = queue.popleft()
        processed += 1

        for nxt in graph[current]:
            candidate = finish_time[current] + duration[nxt]
            if candidate > finish_time[nxt]:
                finish_time[nxt] = candidate

            indegree[nxt] -= 1
            if indegree[nxt] == 0:
                queue.append(nxt)

    if processed < n:
        print("IMPOSSIVEL")
    else:
        print(max(finish_time))


if __name__ == "__main__":
    main()
```

---

# 5. Laboratorio Hamiltoniano

## Ideia Principal

O robo precisa visitar cada sala exatamente uma vez, comecando na sala `0`.

Isso e um problema classico de **programacao dinamica com mascara de bits**.

## Explicacao Para Leigo

Cada conjunto de salas visitadas pode ser representado por um numero binario.

Exemplo com 4 salas:

```text
0101
```

Significa:

- sala 0 visitada;
- sala 1 nao visitada;
- sala 2 visitada;
- sala 3 nao visitada.

O estado da DP e:

```text
dp[mascara][ultima_sala]
```

Ou seja:

> "Qual foi o menor custo para visitar exatamente este conjunto de salas e terminar nesta sala?"

## Passo A Passo

1. Comecar com apenas a sala `0` visitada.
2. Tentar ir para uma sala ainda nao visitada.
3. Atualizar a nova mascara.
4. Repetir ate todas as salas serem visitadas.
5. A resposta e o menor custo entre todos os estados finais.

## Complexidade

```text
Tempo: O(2^N * N^2)
Memoria: O(2^N * N)
```

## Codigo Python

```python
import sys


def main():
    input = sys.stdin.readline
    n = int(input())
    cost = [list(map(int, input().split())) for _ in range(n)]

    full_mask = (1 << n) - 1
    dp = [dict() for _ in range(1 << n)]
    dp[1][0] = 0

    for mask in range(1 << n):
        if not dp[mask]:
            continue

        for current, current_cost in list(dp[mask].items()):
            for nxt in range(n):
                if mask & (1 << nxt):
                    continue

                new_mask = mask | (1 << nxt)
                new_cost = current_cost + cost[current][nxt]

                if nxt not in dp[new_mask] or new_cost < dp[new_mask][nxt]:
                    dp[new_mask][nxt] = new_cost

    print(min(dp[full_mask].values()))


if __name__ == "__main__":
    main()
```

---

# 6. Reinos Fortemente Conectados

## Ideia Principal

O problema pede componentes fortemente conexas em um grafo direcionado.

Duas cidades estao na mesma componente se uma alcanca a outra e a outra tambem alcanca a primeira.

Depois disso, comprimimos cada componente em um unico no e contamos quantas componentes tem grau de entrada zero.

## Explicacao Para Leigo

Imagine grupos de reinos onde todos conseguem ir e voltar entre si.

Cada grupo vira um "super-reino".

Depois olhamos quais super-reinos nao recebem estrada de nenhum outro super-reino.

## Passo A Passo

1. Rodar DFS no grafo original e guardar a ordem de saida.
2. Rodar DFS no grafo invertido seguindo a ordem reversa.
3. Cada DFS no grafo invertido forma uma SCC.
4. Percorrer as arestas originais.
5. Se uma aresta liga SCCs diferentes, aumentar o grau de entrada da SCC destino.
6. Contar SCCs com grau de entrada zero.

## Complexidade

```text
Tempo: O(N + M)
Memoria: O(N + M)
```

## Codigo Python

```python
import sys


def main():
    sys.setrecursionlimit(10**7)
    input = sys.stdin.readline

    n, m = map(int, input().split())
    graph = [[] for _ in range(n + 1)]
    reverse_graph = [[] for _ in range(n + 1)]
    edges = []

    for _ in range(m):
        a, b = map(int, input().split())
        graph[a].append(b)
        reverse_graph[b].append(a)
        edges.append((a, b))

    visited = [False] * (n + 1)
    order = []

    def dfs1(node):
        visited[node] = True
        for nxt in graph[node]:
            if not visited[nxt]:
                dfs1(nxt)
        order.append(node)

    for node in range(1, n + 1):
        if not visited[node]:
            dfs1(node)

    component = [-1] * (n + 1)

    def dfs2(node, component_id):
        component[node] = component_id
        for nxt in reverse_graph[node]:
            if component[nxt] == -1:
                dfs2(nxt, component_id)

    component_count = 0

    for node in reversed(order):
        if component[node] == -1:
            dfs2(node, component_count)
            component_count += 1

    indegree = [0] * component_count

    for a, b in edges:
        ca = component[a]
        cb = component[b]
        if ca != cb:
            indegree[cb] += 1

    answer = sum(1 for value in indegree if value == 0)
    print(answer)


if __name__ == "__main__":
    main()
```

---

# 7. Pontes Da Capital

## Ideia Principal

Uma ponte e uma aresta que, ao ser removida, desconecta o grafo.

O algoritmo classico usa DFS com dois valores:

```text
tin[v] = momento em que v foi visitado
low[v] = menor tin alcancavel a partir de v
```

## Explicacao Para Leigo

Durante a DFS, uma cidade pode ter caminhos alternativos para voltar para uma cidade antiga.

Se um filho nao consegue voltar para nenhum ancestral do pai, entao a estrada entre pai e filho e critica.

## Passo A Passo

1. Fazer DFS no grafo.
2. Marcar o tempo de entrada de cada vertice.
3. Calcular `low`.
4. Para uma aresta de arvore `v -> u`, se:

```text
low[u] > tin[v]
```

entao a aresta e ponte.

## Complexidade

```text
Tempo: O(N + M)
Memoria: O(N + M)
```

## Codigo Python

```python
import sys


def main():
    sys.setrecursionlimit(10**7)
    input = sys.stdin.readline

    n, m = map(int, input().split())
    graph = [[] for _ in range(n + 1)]

    for edge_id in range(m):
        a, b = map(int, input().split())
        graph[a].append((b, edge_id))
        graph[b].append((a, edge_id))

    tin = [-1] * (n + 1)
    low = [0] * (n + 1)
    timer = [0]
    bridges = [0]

    def dfs(node, parent_edge):
        tin[node] = low[node] = timer[0]
        timer[0] += 1

        for nxt, edge_id in graph[node]:
            if edge_id == parent_edge:
                continue

            if tin[nxt] != -1:
                low[node] = min(low[node], tin[nxt])
            else:
                dfs(nxt, edge_id)
                low[node] = min(low[node], low[nxt])

                if low[nxt] > tin[node]:
                    bridges[0] += 1

    for node in range(1, n + 1):
        if tin[node] == -1:
            dfs(node, -1)

    print(bridges[0])


if __name__ == "__main__":
    main()
```

---

# 8. Biblioteca De Subarvores

## Ideia Principal

Para cada no da arvore, precisamos saber quantos temas diferentes existem em sua subarvore.

Uma solucao ingenua criaria um conjunto para cada subarvore do zero, ficando muito lenta.

A tecnica correta e **Small-to-Large**.

## Explicacao Para Leigo

Cada filho entrega um conjunto de temas.

Se voce sempre juntar o conjunto menor dentro do maior, cada tema muda de conjunto poucas vezes.

Isso evita copiar muitos dados repetidamente.

## Passo A Passo

1. Enraizar a arvore no no `1`.
2. Fazer DFS.
3. Cada no comeca com o conjunto contendo seu proprio tema.
4. Para cada filho, receber o conjunto da subarvore dele.
5. Juntar o conjunto menor no maior.
6. A resposta do no e o tamanho do conjunto final.

## Complexidade

```text
Tempo: aproximadamente O(N log N)
Memoria: O(N)
```

## Codigo Python

```python
import sys


def main():
    sys.setrecursionlimit(10**7)
    input = sys.stdin.readline

    n = int(input())
    themes = [0] + list(map(int, input().split()))

    graph = [[] for _ in range(n + 1)]

    for _ in range(n - 1):
        a, b = map(int, input().split())
        graph[a].append(b)
        graph[b].append(a)

    answer = [0] * (n + 1)

    def dfs(node, parent):
        current_set = {themes[node]}

        for child in graph[node]:
            if child == parent:
                continue

            child_set = dfs(child, node)

            if len(child_set) > len(current_set):
                current_set, child_set = child_set, current_set

            current_set.update(child_set)

        answer[node] = len(current_set)
        return current_set

    dfs(1, 0)
    print(*answer[1:])


if __name__ == "__main__":
    main()
```

---

# 9. Trilhas E Ancestrais

## Ideia Principal

O problema pede o maior peso no caminho entre dois vertices de uma arvore.

Como existem muitas consultas, nao podemos subir a arvore passo a passo.

Usamos **Binary Lifting** para encontrar o LCA e, ao mesmo tempo, guardar o maior peso no caminho de subida.

## Explicacao Para Leigo

Em vez de subir um nivel por vez, o algoritmo aprende a subir em saltos:

```text
1, 2, 4, 8, 16, ...
```

Para cada salto, guardamos:

- qual ancestral alcancamos;
- qual foi o maior peso nesse trecho.

## Passo A Passo

1. Fazer uma DFS/BFS a partir da raiz.
2. Guardar profundidade de cada vertice.
3. Guardar o pai imediato e o peso ate ele.
4. Pre-processar ancestrais de tamanho `2^k`.
5. Para consultar `u v`:
   - subir o mais profundo ate a mesma altura;
   - subir os dois juntos ate antes do LCA;
   - acumular o maior peso encontrado.

## Complexidade

```text
Pre-processamento: O(N log N)
Consulta: O(log N)
Memoria: O(N log N)
```

## Codigo Python

```python
import sys


def main():
    input = sys.stdin.readline

    n, q = map(int, input().split())
    graph = [[] for _ in range(n + 1)]

    for _ in range(n - 1):
        a, b, w = map(int, input().split())
        graph[a].append((b, w))
        graph[b].append((a, w))

    log = (n).bit_length()
    parent = [[0] * (n + 1) for _ in range(log)]
    max_edge = [[0] * (n + 1) for _ in range(log)]
    depth = [0] * (n + 1)

    stack = [(1, 0)]
    parent[0][1] = 0

    while stack:
        node, father = stack.pop()

        for nxt, weight in graph[node]:
            if nxt == father:
                continue

            parent[0][nxt] = node
            max_edge[0][nxt] = weight
            depth[nxt] = depth[node] + 1
            stack.append((nxt, node))

    for k in range(1, log):
        for node in range(1, n + 1):
            mid = parent[k - 1][node]
            parent[k][node] = parent[k - 1][mid]
            max_edge[k][node] = max(max_edge[k - 1][node], max_edge[k - 1][mid])

    def query(a, b):
        answer = 0

        if depth[a] < depth[b]:
            a, b = b, a

        difference = depth[a] - depth[b]

        for k in range(log):
            if difference & (1 << k):
                answer = max(answer, max_edge[k][a])
                a = parent[k][a]

        if a == b:
            return answer

        for k in range(log - 1, -1, -1):
            if parent[k][a] != parent[k][b]:
                answer = max(answer, max_edge[k][a], max_edge[k][b])
                a = parent[k][a]
                b = parent[k][b]

        answer = max(answer, max_edge[0][a], max_edge[0][b])
        return answer

    answers = []

    for _ in range(q):
        u, v = map(int, input().split())
        answers.append(str(query(u, v)))

    print("\n".join(answers))


if __name__ == "__main__":
    main()
```

---

# 10. Fronteira Do Campus

## Ideia Principal

O problema pede o fecho convexo dos pontos.

O fecho convexo e a menor cerca convexa que envolve todos os pontos.

Depois precisamos:

- contar quantos pontos ficam na borda;
- calcular o dobro da area.

## Explicacao Para Leigo

Imagine colocar pregos em uma tabua, um prego para cada ponto.

Se voce esticar um elastico ao redor dos pregos, o formato final e o fecho convexo.

Os pontos tocados pelo elastico sao os pontos da fronteira.

## Conceito Matematico

Usamos o produto vetorial para saber se tres pontos fazem uma curva para a esquerda, para a direita ou se estao alinhados.

Para pontos `A`, `B` e `C`:

```text
cross(A, B, C) = (B - A) x (C - A)
```

Se:

```text
cross > 0 -> curva para a esquerda
cross < 0 -> curva para a direita
cross = 0 -> pontos colineares
```

Como pontos colineares na borda devem ser contados, a construcao do hull deve manter pontos alinhados na fronteira.

## Passo A Passo

1. Ordenar os pontos por `x` e depois por `y`.
2. Construir a parte inferior do fecho.
3. Construir a parte superior do fecho.
4. Manter pontos colineares na borda.
5. Calcular a area pelo metodo do cadarco.

## Complexidade

```text
Tempo: O(N log N)
Memoria: O(N)
```

## Codigo Python

```python
import sys


def cross(a, b, c):
    return (b[0] - a[0]) * (c[1] - a[1]) - (b[1] - a[1]) * (c[0] - a[0])


def convex_hull_with_collinear(points):
    points = sorted(set(points))

    if len(points) <= 1:
        return points

    lower = []
    for point in points:
        while len(lower) >= 2 and cross(lower[-2], lower[-1], point) < 0:
            lower.pop()
        lower.append(point)

    upper = []
    for point in reversed(points):
        while len(upper) >= 2 and cross(upper[-2], upper[-1], point) < 0:
            upper.pop()
        upper.append(point)

    hull = lower[:-1] + upper[:-1]
    return hull


def double_area(poly):
    if len(poly) <= 2:
        return 0

    area = 0
    n = len(poly)

    for i in range(n):
        x1, y1 = poly[i]
        x2, y2 = poly[(i + 1) % n]
        area += x1 * y2 - y1 * x2

    return abs(area)


def main():
    input = sys.stdin.readline
    n = int(input())
    points = [tuple(map(int, input().split())) for _ in range(n)]

    hull = convex_hull_with_collinear(points)

    boundary_count = len(set(hull))
    area2 = double_area(hull)

    print(boundary_count, area2)


if __name__ == "__main__":
    main()
```

---

# Observacoes Finais Para O Professor

## Ordem Recomendada Para Explicar Em Aula

Se os alunos ainda estao ganhando maturidade, a melhor ordem de estudo nao e a ordem da lista.

Uma progressao mais didatica seria:

1. Curso Critico;
2. Cofres Complementares;
3. Pontes Da Capital;
4. Reinos Fortemente Conectados;
5. Trilhas E Ancestrais;
6. Arquivos Com Versoes;
7. Pergaminhos E Consultas Imutaveis;
8. Biblioteca De Subarvores;
9. Laboratorio Hamiltoniano;
10. Fronteira Do Campus.

## Como Treinar Os Alunos

Para cada problema, peca que eles respondam antes de programar:

```text
1. Qual seria a solucao ingenua?
2. Por que ela nao passa?
3. Qual estrutura ou algoritmo reduz a complexidade?
4. Qual e o estado, se for DP?
5. Qual e a complexidade final?
6. Qual caso pequeno posso testar manualmente?
```

## Principais Erros Esperados

- esquecer de converter indices de `1` para `0`;
- usar DFS recursiva sem aumentar `sys.setrecursionlimit`;
- tentar resolver problemas de grafo com matriz de adjacencia;
- nao analisar `N` e `Q` antes de escolher o algoritmo;
- usar solucao `O(NQ)` em problemas que exigem `O(log N)` ou `O(1)`;
- confundir grafo direcionado com nao direcionado;
- perder pontos por saida em formato incorreto;
- nao testar casos extremos;
- nao tratar componentes desconexas;
- nao revisar overflow conceitual, mesmo em Python.

## Frase Para Fechar A Aula

Em problemas de nivel senior, programar e a ultima parte. Antes vem a modelagem: entender o tamanho da entrada, escolher a estrutura certa e provar que a complexidade passa.
