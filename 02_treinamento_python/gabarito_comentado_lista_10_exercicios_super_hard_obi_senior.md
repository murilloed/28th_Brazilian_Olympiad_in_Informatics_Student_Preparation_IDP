# Gabarito Comentado - Lista De 10 Exercicios Super Hard

Arquivo referente a:

```text
lista_10_exercicios_super_hard_obi_senior.md
```

Este gabarito foi escrito para explicar os problemas de forma progressiva, como se o leitor ainda estivesse aprendendo a reconhecer a tecnica correta.

Para cada exercicio:

- ideia principal;
- explicacao para leigo;
- passo a passo;
- complexidade;
- codigo Python de referencia.

---

# 1. Arquivo Vivo

## Ideia Principal

Temos duas operacoes:

- somar um valor em um intervalo;
- consultar a soma de um intervalo.

Como `N` e `Q` podem chegar a `200000`, nao podemos atualizar posicao por posicao. Precisamos de uma estrutura que trabalhe por blocos.

A tecnica ideal e **Segment Tree com Lazy Propagation**.

## Explicacao Para Leigo

Imagine uma planilha gigante. Se toda vez que alguem pedir para somar `10` em mil linhas voce alterar uma por uma, o processo fica lento.

A Segment Tree guarda resumos de intervalos.

O Lazy funciona como um bilhete:

```text
Quando alguem precisar olhar dentro deste intervalo, lembre-se de somar X nos filhos.
```

Assim, a atualizacao de um intervalo grande pode ser feita rapidamente.

## Passo A Passo

1. Construir uma arvore onde cada no representa um intervalo.
2. Cada no guarda a soma do seu intervalo.
3. Para atualizar `[L, R]`, se um no estiver completamente dentro, atualizamos sua soma e guardamos o valor lazy.
4. Para consultar `[L, R]`, empurramos pendencias quando necessario.
5. Somamos os trechos que cobrem a consulta.

## Complexidade

```text
Construção: O(N)
Cada operação: O(log N)
Memória: O(N)
```

## Codigo Python

```python
class SegmentTree:
    def __init__(self, v):
        self.n = len(v)
        self.tree = [0] * (4 * self.n)
        self.lazy = [0] * (4 * self.n)
        self._build(1, 0, self.n - 1, v)

    def _build(self, node, l, r, v):
        if l == r:
            self.tree[node] = v[l]
            return

        mid = (l + r) // 2
        self._build(node * 2, l, mid, v)
        self._build(node * 2 + 1, mid + 1, r, v)
        self.tree[node] = self.tree[node * 2] + self.tree[node * 2 + 1]

    def _push(self, node, l, r):
        if self.lazy[node] == 0:
            return

        value = self.lazy[node]
        self.tree[node] += value * (r - l + 1)

        if l != r:
            self.lazy[node * 2] += value
            self.lazy[node * 2 + 1] += value

        self.lazy[node] = 0

    def update(self, node, l, r, ql, qr, value):
        self._push(node, l, r)

        if qr < l or r < ql:
            return

        if ql <= l and r <= qr:
            self.lazy[node] += value
            self._push(node, l, r)
            return

        mid = (l + r) // 2
        self.update(node * 2, l, mid, ql, qr, value)
        self.update(node * 2 + 1, mid + 1, r, ql, qr, value)
        self.tree[node] = self.tree[node * 2] + self.tree[node * 2 + 1]

    def query(self, node, l, r, ql, qr):
        self._push(node, l, r)

        if qr < l or r < ql:
            return 0

        if ql <= l and r <= qr:
            return self.tree[node]

        mid = (l + r) // 2
        left = self.query(node * 2, l, mid, ql, qr)
        right = self.query(node * 2 + 1, mid + 1, r, ql, qr)
        return left + right


n, q = map(int, input().split())
v = list(map(int, input().split()))

seg = SegmentTree(v)

for _ in range(q):
    op = list(map(int, input().split()))

    if op[0] == 1:
        _, l, r, x = op
        seg.update(1, 0, n - 1, l - 1, r - 1, x)
    else:
        _, l, r = op
        print(seg.query(1, 0, n - 1, l - 1, r - 1))
```

---

# 2. Minimo E Maximo Da Jornada

## Ideia Principal

O vetor nao muda. Temos muitas consultas de intervalo.

Quando o vetor e fixo, uma tecnica excelente e **Sparse Table**.

Ela permite consultar minimo e maximo em intervalos rapidamente.

## Explicacao Para Leigo

Imagine que antes da prova voce prepara uma tabela com respostas de blocos:

```text
tamanho 1
tamanho 2
tamanho 4
tamanho 8
...
```

Depois, qualquer intervalo pode ser coberto por dois blocos grandes.

Para saber:

```text
maximo - minimo
```

basta consultar a tabela de maximo e a tabela de minimo.

## Passo A Passo

1. Precalcular `log`.
2. Criar Sparse Table de minimo.
3. Criar Sparse Table de maximo.
4. Para cada consulta `[L, R]`, calcular o tamanho.
5. Usar dois blocos de tamanho `2^k`.
6. Responder `maximo - minimo`.

## Complexidade

```text
Pre-processamento: O(N log N)
Consulta: O(1)
Memória: O(N log N)
```

## Codigo Python

```python
def build_sparse(v, func):
    n = len(v)
    log = [0] * (n + 1)
    for i in range(2, n + 1):
        log[i] = log[i // 2] + 1

    kmax = log[n] + 1
    st = [v[:]]

    for k in range(1, kmax):
        size = 1 << k
        half = size >> 1
        row = []
        prev = st[k - 1]
        for i in range(n - size + 1):
            row.append(func(prev[i], prev[i + half]))
        st.append(row)

    return st, log


def query(st, log, l, r, func):
    length = r - l + 1
    k = log[length]
    return func(st[k][l], st[k][r - (1 << k) + 1])


n, q = map(int, input().split())
v = list(map(int, input().split()))

st_min, log = build_sparse(v, min)
st_max, _ = build_sparse(v, max)

for _ in range(q):
    l, r = map(int, input().split())
    l -= 1
    r -= 1

    mn = query(st_min, log, l, r, min)
    mx = query(st_max, log, l, r, max)
    print(mx - mn)
```

---

# 3. Subconjunto Exato

## Ideia Principal

Queremos contar subconjuntos com soma `S`.

Com `N <= 40`, testar todos os subconjuntos seria:

```text
2^40
```

Isso e grande demais.

Usamos **Meet-in-the-Middle**:

- divide em duas metades;
- gera somas da metade esquerda;
- gera somas da metade direita;
- combina as somas.

## Explicacao Para Leigo

Em vez de abrir uma porta gigante de uma vez, abrimos duas portas menores.

`40` elementos geram muitos subconjuntos. Mas `20` elementos geram cerca de um milhao, que ainda e viavel.

Depois perguntamos:

```text
se a metade esquerda soma X, quantas somas da direita valem S - X?
```

## Passo A Passo

1. Dividir o vetor em duas partes.
2. Gerar todas as somas da primeira metade.
3. Gerar todas as somas da segunda metade.
4. Contar as somas da segunda metade com `Counter`.
5. Para cada soma da primeira, procurar o complemento.

## Complexidade

```text
O(2^(N/2))
```

## Codigo Python

```python
from collections import Counter


def gerar_somas(v):
    somas = [0]
    for x in v:
        novas = [s + x for s in somas]
        somas += novas
    return somas


n, alvo = map(int, input().split())
v = list(map(int, input().split()))

meio = n // 2
esq = v[:meio]
dir = v[meio:]

somas_esq = gerar_somas(esq)
somas_dir = Counter(gerar_somas(dir))

resposta = 0

for s in somas_esq:
    resposta += somas_dir[alvo - s]

print(resposta)
```

---

# 4. Rotas Com Pedagio Negativo

## Ideia Principal

Temos grafo direcionado com pesos negativos.

Dijkstra nao funciona com pesos negativos.

Usamos **Bellman-Ford**, que tambem detecta ciclo negativo.

## Explicacao Para Leigo

O algoritmo tenta melhorar todas as estradas varias vezes.

Se depois de `N - 1` rodadas ainda for possivel melhorar alguma distancia, isso indica um ciclo negativo.

Um ciclo negativo permite reduzir o custo infinitamente, entao nao existe uma resposta normal.

## Passo A Passo

1. Inicializar distancia da cidade `1` como `0`.
2. Repetir `N - 1` vezes:
   - tentar relaxar todas as arestas.
3. Fazer uma rodada extra.
4. Se alguma distancia ainda melhora, existe ciclo negativo alcancavel.

## Complexidade

```text
O(NM)
```

## Codigo Python

```python
n, m = map(int, input().split())
arestas = []

for _ in range(m):
    a, b, c = map(int, input().split())
    arestas.append((a, b, c))

INF = 10**30
dist = [INF] * (n + 1)
dist[1] = 0

for _ in range(n - 1):
    mudou = False
    for a, b, c in arestas:
        if dist[a] != INF and dist[a] + c < dist[b]:
            dist[b] = dist[a] + c
            mudou = True
    if not mudou:
        break

ciclo = False
for a, b, c in arestas:
    if dist[a] != INF and dist[a] + c < dist[b]:
        ciclo = True
        break

if ciclo:
    print("CICLO NEGATIVO")
else:
    saida = []
    for i in range(1, n + 1):
        saida.append("INF" if dist[i] == INF else str(dist[i]))
    print(" ".join(saida))
```

---

# 5. Grupos Secretos

## Ideia Principal

Queremos identificar **componentes fortemente conexas** em grafo direcionado.

Duas bases estao no mesmo grupo se:

```text
A chega em B
B chega em A
```

Usaremos **Kosaraju**.

## Explicacao Para Leigo

Em grafo nao direcionado, basta estar conectado.

Em grafo direcionado, a direcao importa. Pode existir caminho de ida sem caminho de volta.

Kosaraju resolve isso com duas passagens de DFS:

1. uma no grafo original;
2. outra no grafo invertido.

## Passo A Passo

1. Fazer DFS no grafo original e guardar ordem de termino.
2. Inverter todas as arestas.
3. Processar vertices na ordem reversa.
4. Cada DFS no grafo invertido forma uma SCC.

## Complexidade

```text
O(N + M)
```

## Codigo Python

```python
import sys
sys.setrecursionlimit(10**7)

n, m = map(int, input().split())
g = [[] for _ in range(n + 1)]
gr = [[] for _ in range(n + 1)]

for _ in range(m):
    a, b = map(int, input().split())
    g[a].append(b)
    gr[b].append(a)

vis = [False] * (n + 1)
ordem = []

def dfs(v):
    vis[v] = True
    for u in g[v]:
        if not vis[u]:
            dfs(u)
    ordem.append(v)

def dfs_rev(v, comp_id):
    comp[v] = comp_id
    for u in gr[v]:
        if comp[u] == 0:
            dfs_rev(u, comp_id)

for i in range(1, n + 1):
    if not vis[i]:
        dfs(i)

comp = [0] * (n + 1)
comp_id = 0

for v in reversed(ordem):
    if comp[v] == 0:
        comp_id += 1
        dfs_rev(v, comp_id)

print(*comp[1:])
```

---

# 6. Ancestrais Do Reino

## Ideia Principal

Precisamos responder varias consultas de LCA:

```text
menor ancestral comum entre u e v
```

Subir um pai por vez seria lento.

Usamos **Binary Lifting**.

## Explicacao Para Leigo

Em vez de subir um degrau por vez na arvore, preparamos pulos:

```text
1, 2, 4, 8, 16...
```

Assim, conseguimos subir rapidamente.

## Passo A Passo

1. Fazer DFS a partir da raiz.
2. Guardar profundidade de cada vertice.
3. Guardar `up[v][k]`, o ancestral de `v` a distancia `2^k`.
4. Para consultar:
   - igualar profundidades;
   - subir os dois juntos ate quase encontrarem o LCA.

## Complexidade

```text
Pre-processamento: O(N log N)
Consulta: O(log N)
```

## Codigo Python

```python
import sys
sys.setrecursionlimit(10**7)

n, q = map(int, input().split())
LOG = (n + 1).bit_length()

g = [[] for _ in range(n + 1)]

for _ in range(n - 1):
    a, b = map(int, input().split())
    g[a].append(b)
    g[b].append(a)

up = [[0] * LOG for _ in range(n + 1)]
depth = [0] * (n + 1)

def dfs(v, p):
    up[v][0] = p
    for k in range(1, LOG):
        up[v][k] = up[up[v][k - 1]][k - 1]

    for u in g[v]:
        if u != p:
            depth[u] = depth[v] + 1
            dfs(u, v)

def lca(a, b):
    if depth[a] < depth[b]:
        a, b = b, a

    diff = depth[a] - depth[b]
    for k in range(LOG):
        if diff & (1 << k):
            a = up[a][k]

    if a == b:
        return a

    for k in range(LOG - 1, -1, -1):
        if up[a][k] != up[b][k]:
            a = up[a][k]
            b = up[b][k]

    return up[a][0]

dfs(1, 1)

for _ in range(q):
    u, v = map(int, input().split())
    print(lca(u, v))
```

---

# 7. Cores Das Subarvores

## Ideia Principal

Para cada vertice, queremos saber quantas cores diferentes existem em sua subarvore.

Se juntarmos conjuntos ingenuamente, pode ficar `O(N^2)`.

Usamos **Small-to-Large**.

## Explicacao Para Leigo

Cada filho devolve um conjunto de cores.

Ao juntar conjuntos, sempre colocamos o menor dentro do maior.

Isso evita copiar muitos elementos muitas vezes.

## Passo A Passo

1. Fazer DFS.
2. Cada vertice comeca com um conjunto contendo sua propria cor.
3. Para cada filho, pegar o conjunto dele.
4. Se o conjunto do filho for maior, trocar.
5. Inserir os elementos do menor no maior.
6. A resposta do vertice e o tamanho do conjunto final.

## Complexidade

```text
O(N log N) aproximadamente
```

Na pratica, eficiente para `N` grande.

## Codigo Python

```python
import sys
sys.setrecursionlimit(10**7)

n = int(input())
cor = [0] + list(map(int, input().split()))

g = [[] for _ in range(n + 1)]

for _ in range(n - 1):
    a, b = map(int, input().split())
    g[a].append(b)
    g[b].append(a)

ans = [0] * (n + 1)

def dfs(v, p):
    atual = {cor[v]}

    for u in g[v]:
        if u == p:
            continue

        filho = dfs(u, v)

        if len(filho) > len(atual):
            atual, filho = filho, atual

        atual.update(filho)

    ans[v] = len(atual)
    return atual

dfs(1, 0)
print(*ans[1:])
```

---

# 8. Entregas Com Mascara

## Ideia Principal

Temos ate `N = 20`.

Isso sugere **DP com mascara de bits**.

Cada mascara representa quais cidades ja foram visitadas.

## Explicacao Para Leigo

Uma mascara e um conjunto compactado em binario.

Exemplo:

```text
1011
```

significa que as cidades `0`, `1` e `3` ja foram visitadas.

O estado sera:

```text
dp[mask][u] = menor custo para visitar mask e terminar em u
```

## Passo A Passo

1. Comecar com `dp[1][0] = 0`, pois visitamos apenas a cidade 0.
2. Para cada mascara, tentar sair da ultima cidade `u`.
3. Ir para uma cidade ainda nao visitada `v`.
4. Atualizar o novo estado.

## Complexidade

```text
O(2^N * N^2)
```

## Codigo Python

```python
n = int(input())
c = [list(map(int, input().split())) for _ in range(n)]

INF = 10**30
dp = [[INF] * n for _ in range(1 << n)]
dp[1][0] = 0

for mask in range(1 << n):
    for u in range(n):
        if dp[mask][u] == INF:
            continue

        for v in range(n):
            if mask & (1 << v):
                continue

            new_mask = mask | (1 << v)
            dp[new_mask][v] = min(dp[new_mask][v], dp[mask][u] + c[u][v])

full = (1 << n) - 1
print(min(dp[full]))
```

---

# 9. Ponto Dentro Da Fortaleza

## Ideia Principal

Para saber se um ponto esta dentro de um poligono, usamos **Ray Casting**.

Tambem precisamos tratar se o ponto esta exatamente na borda.

## Explicacao Para Leigo

Imagine desenhar um raio horizontal saindo do ponto para a direita.

Se ele cruza a borda do poligono um numero impar de vezes, o ponto esta dentro.

Se cruza um numero par, esta fora.

Antes disso, verificamos se o ponto esta em cima de algum segmento da borda.

## Passo A Passo

1. Para cada aresta do poligono:
   - verificar se o ponto esta na borda;
   - se nao estiver, verificar cruzamento do raio.
2. Alternar o estado `dentro` a cada cruzamento valido.
3. Imprimir `DENTRO` ou `FORA`.

## Complexidade

```text
O(N * Q)
```

Observacao: para limites muito altos, seria necessario tecnica mais avancada. Este codigo e didatico e correto para instancias moderadas.

## Codigo Python

```python
def cross(a, b, c):
    return (b[0] - a[0]) * (c[1] - a[1]) - (b[1] - a[1]) * (c[0] - a[0])

def on_segment(a, b, p):
    if cross(a, b, p) != 0:
        return False

    return (
        min(a[0], b[0]) <= p[0] <= max(a[0], b[0])
        and min(a[1], b[1]) <= p[1] <= max(a[1], b[1])
    )

def inside(poly, p):
    n = len(poly)
    x, y = p
    dentro = False

    for i in range(n):
        a = poly[i]
        b = poly[(i + 1) % n]

        if on_segment(a, b, p):
            return True

        x1, y1 = a
        x2, y2 = b

        cruza = (y1 > y) != (y2 > y)

        if cruza:
            x_inter = x1 + (y - y1) * (x2 - x1) / (y2 - y1)
            if x_inter > x:
                dentro = not dentro

    return dentro


n, q = map(int, input().split())
poly = [tuple(map(int, input().split())) for _ in range(n)]

for _ in range(q):
    p = tuple(map(int, input().split()))
    print("DENTRO" if inside(poly, p) else "FORA")
```

---

# 10. Muralha Externa

## Ideia Principal

Precisamos calcular o **Convex Hull**, que e o menor poligono convexo que envolve todos os pontos.

Depois calculamos o perimetro.

## Explicacao Para Leigo

Imagine passar um elastico em volta dos pontos.

Os pontos tocados pelo elastico formam a borda externa.

Depois de encontrar essa borda, somamos as distancias entre pontos consecutivos.

## Passo A Passo

1. Ordenar os pontos.
2. Construir a parte de baixo do fecho.
3. Construir a parte de cima do fecho.
4. Juntar as duas partes.
5. Somar as distancias dos lados.

## Complexidade

```text
O(N log N)
```

## Codigo Python

```python
import math

def cross(o, a, b):
    return (a[0] - o[0]) * (b[1] - o[1]) - (a[1] - o[1]) * (b[0] - o[0])

def convex_hull(points):
    points = sorted(set(points))

    if len(points) <= 1:
        return points

    lower = []
    for p in points:
        while len(lower) >= 2 and cross(lower[-2], lower[-1], p) <= 0:
            lower.pop()
        lower.append(p)

    upper = []
    for p in reversed(points):
        while len(upper) >= 2 and cross(upper[-2], upper[-1], p) <= 0:
            upper.pop()
        upper.append(p)

    return lower[:-1] + upper[:-1]

def dist(a, b):
    return math.hypot(a[0] - b[0], a[1] - b[1])


n = int(input())
points = [tuple(map(int, input().split())) for _ in range(n)]

hull = convex_hull(points)

if len(hull) == 1:
    print("0.000000")
else:
    perimetro = 0
    for i in range(len(hull)):
        perimetro += dist(hull[i], hull[(i + 1) % len(hull)])

    print(f"{perimetro:.6f}")
```

---

# Observacao Final

Esses 10 exercicios sao de nivel alto porque exigem que o aluno reconheca rapidamente:

- quando usar estrutura de intervalo;
- quando dividir busca em metades;
- quando grafo precisa de algoritmo especializado;
- quando uma arvore precisa de pre-processamento;
- quando geometria exige tratamento de casos de borda.

O treino ideal e resolver primeiro sem olhar o codigo, depois comparar a ideia com o gabarito.

