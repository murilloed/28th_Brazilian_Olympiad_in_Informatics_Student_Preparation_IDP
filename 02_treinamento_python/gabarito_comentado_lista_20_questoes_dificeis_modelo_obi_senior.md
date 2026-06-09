# Gabarito Comentado - Lista De 20 Questoes Dificeis

Arquivo referente a:

```text
lista_20_questoes_dificeis_modelo_obi_senior.md
```

Este material explica as solucoes de forma didatica, pensando em alunos que ainda estao formando base em algoritmos.

Para cada exercicio, a estrutura sera:

- ideia principal;
- explicacao para leigo;
- passo a passo;
- complexidade;
- codigo Python de referencia.

---

# 1. Fotos Do Festival

## Ideia Principal

Contar quantos intervalos possuem exatamente um `1`.

Em vez de testar todos os intervalos, olhamos para cada posicao que tem `1` e contamos quantos intervalos podem escolher aquele `1` como o unico destaque.

## Explicacao Para Leigo

Imagine que cada `1` e uma decoracao especial. Para uma foto ter exatamente uma decoracao, ela pode comecar em qualquer posicao depois do `1` anterior e terminar antes do proximo `1`.

Se existe um `1` na posicao `p`:

- escolhas de inicio = distancia ate o `1` anterior;
- escolhas de fim = distancia ate o proximo `1`;
- intervalos gerados por esse `1` = inicio * fim.

## Passo A Passo

1. Guardar as posicoes onde aparece `1`.
2. Colocar sentinelas:
   - `-1` antes do primeiro indice;
   - `n` depois do ultimo indice.
3. Para cada `1`, calcular:

```text
(posicao_atual - posicao_anterior) * (proxima_posicao - posicao_atual)
```

4. Somar tudo.

## Complexidade

```text
O(N)
```

## Codigo Python

```python
n = int(input())
a = list(map(int, input().split()))

pos = [-1]

for i, x in enumerate(a):
    if x == 1:
        pos.append(i)

pos.append(n)

resposta = 0

for i in range(1, len(pos) - 1):
    esquerda = pos[i] - pos[i - 1]
    direita = pos[i + 1] - pos[i]
    resposta += esquerda * direita

print(resposta)
```

---

# 2. Escada Restaurada

## Ideia Principal

Cada altura conhecida cria um limite para as outras posicoes.

Se uma posicao conhecida tem altura `h` no indice `i`, entao uma posicao `j` nao pode ter altura maior que:

```text
h + |i - j|
```

porque a altura so pode variar 1 por degrau.

## Explicacao Para Leigo

Pense que a altura conhecida espalha uma "montanha" para os lados. A cada passo para longe, o valor pode aumentar no maximo 1.

Se o degrau 1 tem altura 5:

```text
posicao: 1 2 3 4
maximo:  5 6 7 8
```

Se tambem houver uma altura conhecida do outro lado, pegamos o menor limite imposto pelos dois lados.

## Observacao Importante

Para a resposta ser finita, assumimos que alturas restauradas nao passam de `10^9`, coerente com o limite dos valores conhecidos.

Se todos os degraus forem desconhecidos, a maior resposta sera todos com `10^9`.

## Passo A Passo

1. Criar um vetor `limite` com valor grande.
2. Nas posicoes conhecidas, colocar a propria altura.
3. Passar da esquerda para a direita:
   - cada posicao pode ser no maximo a anterior + 1.
4. Passar da direita para a esquerda:
   - cada posicao pode ser no maximo a proxima + 1.
5. Verificar se as posicoes conhecidas continuam corretas.
6. Verificar se diferencas consecutivas sao no maximo 1.

## Complexidade

```text
O(N)
```

## Codigo Python

```python
n = int(input())
a = list(map(int, input().split()))

MAX_H = 10**9
INF = 10**30

limite = [INF] * n

tem_conhecido = False

for i, x in enumerate(a):
    if x != -1:
        limite[i] = x
        tem_conhecido = True

if not tem_conhecido:
    print(*([MAX_H] * n))
else:
    for i in range(1, n):
        limite[i] = min(limite[i], limite[i - 1] + 1)

    for i in range(n - 2, -1, -1):
        limite[i] = min(limite[i], limite[i + 1] + 1)

    resposta = []
    ok = True

    for i in range(n):
        if a[i] != -1 and limite[i] != a[i]:
            ok = False
        resposta.append(min(limite[i], MAX_H))

    for i in range(n - 1):
        if abs(resposta[i] - resposta[i + 1]) > 1:
            ok = False

    if ok:
        print(*resposta)
    else:
        print("IMPOSSIVEL")
```

---

# 3. Pontes Antigas

## Ideia Principal

Queremos manter uma rede sem ciclos e conectada, ou seja, uma arvore.

Conexoes do tipo `1` nao podem ser removidas. Entao, se elas ja formarem ciclo, a resposta e `N`.

Depois, usamos conexoes do tipo `2` para conectar o que falta. As conexoes do tipo `2` que criariam ciclo podem ser removidas. Contamos quantas remocoes desse tipo seriam necessarias.

## Explicacao Para Leigo

Uma arvore e uma rede com todos conectados e sem caminho sobrando.

Se uma estrada cria um ciclo, ela e redundante.

O Union-Find ajuda a responder rapidamente:

```text
essas duas ilhas ja estao conectadas?
```

Se ja estao conectadas, adicionar essa estrada cria ciclo.

## Passo A Passo

1. Inicializar Union-Find.
2. Processar primeiro as conexoes tipo `1`.
3. Se uma tipo `1` cria ciclo, impossivel.
4. Processar conexoes tipo `2`.
5. Se uma tipo `2` cria ciclo, ela pode ser removida.
6. Verificar se todas as ilhas ficaram conectadas.
7. Verificar se remocoes de tipo `2` nao passam de `K`.

## Complexidade

```text
O(M log* N)
```

Na pratica, quase linear.

## Codigo Python

```python
class DSU:
    def __init__(self, n):
        self.pai = list(range(n + 1))
        self.tam = [1] * (n + 1)

    def find(self, x):
        while self.pai[x] != x:
            self.pai[x] = self.pai[self.pai[x]]
            x = self.pai[x]
        return x

    def union(self, a, b):
        a = self.find(a)
        b = self.find(b)
        if a == b:
            return False
        if self.tam[a] < self.tam[b]:
            a, b = b, a
        self.pai[b] = a
        self.tam[a] += self.tam[b]
        return True


n, m, k = map(int, input().split())
tipo1 = []
tipo2 = []

for _ in range(m):
    a, b, t = map(int, input().split())
    if t == 1:
        tipo1.append((a, b))
    else:
        tipo2.append((a, b))

dsu = DSU(n)
ok = True

for a, b in tipo1:
    if not dsu.union(a, b):
        ok = False

remocoes = 0

for a, b in tipo2:
    if not dsu.union(a, b):
        remocoes += 1

raiz = dsu.find(1)
for i in range(2, n + 1):
    if dsu.find(i) != raiz:
        ok = False

if ok and remocoes <= k:
    print("S")
else:
    print("N")
```

---

# 4. Harmonia De Sinais

## Ideia Principal

Cada sinal tem pontuacao original:

```text
A_i - B_i
```

Se zerarmos a resistencia, ele vira:

```text
A_i
```

O ganho de zerar a resistencia e `B_i`. Mas so vale escolher sinais que ajudem a maximizar a soma final.

## Explicacao Para Leigo

Para cada sinal, existem duas possibilidades:

1. nao mexer nele;
2. gastar uma alteracao para remover a resistencia.

Se a pontuacao original ja e positiva, ela ja entra na soma.

Se zerar a resistencia melhora o resultado, guardamos esse ganho e escolhemos os melhores `K`.

## Passo A Passo

1. Para cada sinal, calcular valor sem mudanca.
2. Se positivo, adicionar na resposta base.
3. Calcular quanto melhoraria se a resistencia fosse zerada.
4. Guardar os ganhos positivos.
5. Ordenar ganhos em ordem decrescente.
6. Somar os `K` maiores.

## Complexidade

```text
O(N log N)
```

## Codigo Python

```python
n, k = map(int, input().split())
a = list(map(int, input().split()))
b = list(map(int, input().split()))

base = 0
ganhos = []

for ai, bi in zip(a, b):
    sem_mudar = ai - bi
    mudado = ai

    if sem_mudar > 0:
        base += sem_mudar

    ganho = mudado - max(0, sem_mudar)

    if ganho > 0:
        ganhos.append(ganho)

ganhos.sort(reverse=True)

resposta = base + sum(ganhos[:k])

print(resposta)
```

---

# 5. Energia Entre Torres

## Ideia Principal

Queremos maximizar:

```text
|i - j| + |A_i - A_j|
```

Para `i < j`, temos:

```text
j - i + |A_j - A_i|
```

O modulo gera dois casos:

```text
j - i + A_j - A_i = (A_j + j) - (A_i + i)
j - i + A_i - A_j = (j - A_j) - (i - A_i)
```

## Explicacao Para Leigo

O modulo atrapalha. Entao separamos em duas formulas.

Em cada formula, queremos:

```text
maior valor da direita - menor valor da esquerda
```

Percorremos da esquerda para a direita guardando os menores valores vistos.

## Passo A Passo

1. Para cada posicao, calcular:
   - `A_i + i`;
   - `i - A_i`.
2. Manter o menor desses valores ja vistos.
3. Atualizar resposta com a diferenca.

## Complexidade

```text
O(N)
```

## Codigo Python

```python
n = int(input())
a = list(map(int, input().split()))

INF = 10**30

menor1 = INF
menor2 = INF
resp = 0

for idx, ai in enumerate(a, start=1):
    val1 = ai + idx
    val2 = idx - ai

    resp = max(resp, val1 - menor1)
    resp = max(resp, val2 - menor2)

    menor1 = min(menor1, val1)
    menor2 = min(menor2, val2)

print(resp)
```

---

# 6. Consultas De Energia

## Ideia Principal

A energia maxima dentro de `[L, R]` tambem pode ser transformada usando quatro expressoes:

```text
A_i + i
A_i - i
-A_i + i
-A_i - i
```

Para um intervalo, a maior distancia tipo Manhattan em 1D+altura pode ser calculada por:

```text
max(expressao) - min(expressao)
```

para as expressoes adequadas.

## Explicacao Para Leigo

Cada torre pode ser vista como um ponto:

```text
(posicao, altura)
```

A energia e uma distancia de Manhattan:

```text
|x1 - x2| + |y1 - y2|
```

Para responder muitas consultas, precisamos consultar maximos e minimos rapidamente.

## Estrategia

Usar Sparse Table ou Segment Tree para maximo e minimo das quatro expressoes.

Aqui usaremos Segment Tree iterativa para simplificar.

## Complexidade

```text
Construcao: O(N)
Consulta: O(log N)
```

## Codigo Python

```python
class Seg:
    def __init__(self, v, op, neutro):
        self.n = len(v)
        self.op = op
        self.neutro = neutro
        self.seg = [neutro] * (2 * self.n)
        for i, x in enumerate(v):
            self.seg[self.n + i] = x
        for i in range(self.n - 1, 0, -1):
            self.seg[i] = op(self.seg[2 * i], self.seg[2 * i + 1])

    def query(self, l, r):
        l += self.n
        r += self.n
        ans = self.neutro
        while l <= r:
            if l % 2 == 1:
                ans = self.op(ans, self.seg[l])
                l += 1
            if r % 2 == 0:
                ans = self.op(ans, self.seg[r])
                r -= 1
            l //= 2
            r //= 2
        return ans


n, q = map(int, input().split())
a = list(map(int, input().split()))

exprs = []
for s1, s2 in [(1, 1), (1, -1), (-1, 1), (-1, -1)]:
    exprs.append([s1 * (i + 1) + s2 * a[i] for i in range(n)])

maxsegs = [Seg(v, max, -10**30) for v in exprs]
minsegs = [Seg(v, min, 10**30) for v in exprs]

for _ in range(q):
    l, r = map(int, input().split())
    l -= 1
    r -= 1
    resp = 0
    for i in range(4):
        resp = max(resp, maxsegs[i].query(l, r) - minsegs[i].query(l, r))
    print(resp)
```

---

# 7. Mapa De Trilhas

## Ideia Principal

Precisamos conectar todas as cidades com custo minimo.

Isso e uma Arvore Geradora Minima.

O algoritmo de Kruskal resolve:

1. ordenar arestas por custo;
2. ir escolhendo as menores que nao formam ciclo.

## Explicacao Para Leigo

Imagine que voce quer conectar todas as cidades gastando o minimo.

Voce sempre tenta usar a estrada mais barata ainda disponivel.

Mas se ela liga cidades que ja estao conectadas, ela criaria ciclo e nao e necessaria.

## Complexidade

```text
O(M log M)
```

## Codigo Python

```python
class DSU:
    def __init__(self, n):
        self.p = list(range(n + 1))
        self.t = [1] * (n + 1)

    def find(self, x):
        while self.p[x] != x:
            self.p[x] = self.p[self.p[x]]
            x = self.p[x]
        return x

    def union(self, a, b):
        a = self.find(a)
        b = self.find(b)
        if a == b:
            return False
        if self.t[a] < self.t[b]:
            a, b = b, a
        self.p[b] = a
        self.t[a] += self.t[b]
        return True


n, m = map(int, input().split())
arestas = []

for _ in range(m):
    a, b, c = map(int, input().split())
    arestas.append((c, a, b))

arestas.sort()
dsu = DSU(n)
total = 0
usadas = 0

for c, a, b in arestas:
    if dsu.union(a, b):
        total += c
        usadas += 1

if usadas == n - 1:
    print(total)
else:
    print("IMPOSSIVEL")
```

---

# 8. Rotas Com Desconto

## Ideia Principal

Como existem custos negativos, Dijkstra nao serve.

Usamos Bellman-Ford.

## Explicacao Para Leigo

O Bellman-Ford tenta melhorar todos os caminhos varias vezes.

Com `N` cidades, o menor caminho simples tem no maximo `N - 1` arestas.

Por isso repetimos o relaxamento `N - 1` vezes.

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

saida = []
for i in range(1, n + 1):
    if dist[i] == INF:
        saida.append("INF")
    else:
        saida.append(str(dist[i]))

print(" ".join(saida))
```

---

# 9. Ordem Das Tarefas

## Ideia Principal

Precisamos ordenar tarefas respeitando pre-requisitos.

Isso e Ordenacao Topologica.

## Explicacao Para Leigo

Uma tarefa so pode ser feita quando todas as anteriores ja foram feitas.

Comecamos pelas tarefas com grau de entrada zero, ou seja, que nao dependem de nenhuma outra.

## Complexidade

```text
O(N + M)
```

## Codigo Python

```python
from collections import deque

n, m = map(int, input().split())
g = [[] for _ in range(n + 1)]
grau = [0] * (n + 1)

for _ in range(m):
    a, b = map(int, input().split())
    g[a].append(b)
    grau[b] += 1

fila = deque()
for i in range(1, n + 1):
    if grau[i] == 0:
        fila.append(i)

ordem = []

while fila:
    v = fila.popleft()
    ordem.append(v)
    for u in g[v]:
        grau[u] -= 1
        if grau[u] == 0:
            fila.append(u)

if len(ordem) == n:
    print(*ordem)
else:
    print("IMPOSSIVEL")
```

---

# 10. Caminho Mais Longo Sem Ciclos

## Ideia Principal

Em DAG, podemos usar DP na ordem topologica.

## Explicacao Para Leigo

Se nao existem ciclos, podemos processar primeiro quem vem antes.

Para cada aresta `v -> u`, se o melhor caminho ate `v` tem tamanho `dp[v]`, entao o caminho ate `u` pode melhorar para:

```text
dp[v] + 1
```

## Complexidade

```text
O(N + M)
```

## Codigo Python

```python
from collections import deque

n, m = map(int, input().split())
g = [[] for _ in range(n + 1)]
grau = [0] * (n + 1)

for _ in range(m):
    a, b = map(int, input().split())
    g[a].append(b)
    grau[b] += 1

fila = deque([i for i in range(1, n + 1) if grau[i] == 0])
ordem = []

while fila:
    v = fila.popleft()
    ordem.append(v)
    for u in g[v]:
        grau[u] -= 1
        if grau[u] == 0:
            fila.append(u)

dp = [0] * (n + 1)

for v in ordem:
    for u in g[v]:
        dp[u] = max(dp[u], dp[v] + 1)

print(max(dp))
```

---

# 11. Senhas Possiveis

## Ideia Principal

Cada `?` pode virar 26 letras.

Se existem `q` interrogacoes, a resposta e:

```text
26^q
```

modulo `10^9 + 7`.

## Explicacao Para Leigo

Se ha 1 ponto desconhecido, ha 26 opcoes.

Se ha 2, ha:

```text
26 * 26
```

Se ha `q`, ha:

```text
26^q
```

## Complexidade

```text
O(N)
```

## Codigo Python

```python
MOD = 10**9 + 7

s = input().strip()
q = s.count("?")

print(pow(26, q, MOD))
```

---

# 12. Escolha De Equipe

## Ideia Principal

Precisamos calcular:

```text
C(N, K) = N! / (K! * (N-K)!)
```

Como ha modulo primo, usamos inverso modular.

## Explicacao Para Leigo

Dividir em modulo nao e uma divisao normal.

Para dividir por `x`, multiplicamos pelo inverso modular de `x`.

Em modulo primo:

```text
inverso(x) = x^(MOD-2) mod MOD
```

## Complexidade

```text
O(N)
```

## Codigo Python

```python
MOD = 10**9 + 7

n, k = map(int, input().split())

fat = [1] * (n + 1)
for i in range(1, n + 1):
    fat[i] = fat[i - 1] * i % MOD

def inv(x):
    return pow(x, MOD - 2, MOD)

resp = fat[n]
resp = resp * inv(fat[k]) % MOD
resp = resp * inv(fat[n - k]) % MOD

print(resp)
```

---

# 13. Sequencia Crescente

## Ideia Principal

Queremos a LIS: maior subsequencia crescente.

Usamos uma lista `tails`, onde `tails[t]` guarda o menor final possivel para uma subsequencia de tamanho `t + 1`.

## Explicacao Para Leigo

Nao precisamos guardar a subsequencia inteira.

So guardamos o melhor final possivel para cada tamanho.

Quanto menor o final, maior a chance de continuar crescendo depois.

## Complexidade

```text
O(N log N)
```

## Codigo Python

```python
from bisect import bisect_left

n = int(input())
a = list(map(int, input().split()))

tails = []

for x in a:
    pos = bisect_left(tails, x)
    if pos == len(tails):
        tails.append(x)
    else:
        tails[pos] = x

print(len(tails))
```

---

# 14. Moedas Raras

## Ideia Principal

DP de contagem.

`dp[s]` representa quantas formas existem de formar soma `s`.

Como cada moeda pode ser usada varias vezes, percorremos as somas em ordem crescente para cada moeda.

## Explicacao Para Leigo

Comecamos com:

```text
existe 1 forma de fazer soma 0: escolher nada
```

Depois, para cada moeda, atualizamos as somas que ela pode formar.

## Complexidade

```text
O(N*S)
```

## Codigo Python

```python
MOD = 10**9 + 7

n, s = map(int, input().split())
moedas = list(map(int, input().split()))

dp = [0] * (s + 1)
dp[0] = 1

for moeda in moedas:
    for valor in range(moeda, s + 1):
        dp[valor] = (dp[valor] + dp[valor - moeda]) % MOD

print(dp[s])
```

---

# 15. Submatriz Valiosa

## Ideia Principal

Usar soma de prefixo 2D.

Assim, a soma de qualquer retangulo pode ser respondida em `O(1)`.

## Explicacao Para Leigo

Criamos uma matriz auxiliar onde cada posicao guarda a soma de tudo que esta acima e a esquerda.

Para pegar um retangulo, usamos inclusao-exclusao:

```text
total grande - parte de cima - parte esquerda + parte removida duas vezes
```

## Complexidade

```text
Pre-processamento: O(N*M)
Consulta: O(1)
```

## Codigo Python

```python
n, m, q = map(int, input().split())
mat = [list(map(int, input().split())) for _ in range(n)]

pref = [[0] * (m + 1) for _ in range(n + 1)]

for i in range(1, n + 1):
    for j in range(1, m + 1):
        pref[i][j] = (
            mat[i - 1][j - 1]
            + pref[i - 1][j]
            + pref[i][j - 1]
            - pref[i - 1][j - 1]
        )

for _ in range(q):
    x1, y1, x2, y2 = map(int, input().split())
    ans = (
        pref[x2][y2]
        - pref[x1 - 1][y2]
        - pref[x2][y1 - 1]
        + pref[x1 - 1][y1 - 1]
    )
    print(ans)
```

---

# 16. Guardas Na Muralha

## Ideia Principal

Ordenar intervalos e juntar os que se sobrepoem.

## Explicacao Para Leigo

Se dois guardas cobrem:

```text
[1, 4] e [3, 6]
```

na pratica a cobertura junta vira:

```text
[1, 6]
```

Depois somamos os tamanhos dos intervalos unidos.

## Complexidade

```text
O(M log M)
```

## Codigo Python

```python
n, m = map(int, input().split())
intervalos = []

for _ in range(m):
    l, r = map(int, input().split())
    intervalos.append((l, r))

intervalos.sort()

total = 0
atual_l = -1
atual_r = -1

for l, r in intervalos:
    if atual_l == -1:
        atual_l, atual_r = l, r
    elif l <= atual_r + 1:
        atual_r = max(atual_r, r)
    else:
        total += atual_r - atual_l + 1
        atual_l, atual_r = l, r

if atual_l != -1:
    total += atual_r - atual_l + 1

print(total)
```

---

# 17. Labirinto De Cristal

## Ideia Principal

Menor caminho em grid sem pesos: usar BFS.

## Explicacao Para Leigo

BFS anda em ondas.

Primeiro visita tudo a distancia 1, depois distancia 2, depois distancia 3.

Quando chega no destino, a distancia encontrada e a menor possivel.

## Complexidade

```text
O(N*M)
```

## Codigo Python

```python
from collections import deque

n, m = map(int, input().split())
grid = [list(input().strip()) for _ in range(n)]

inicio = fim = None

for i in range(n):
    for j in range(m):
        if grid[i][j] == "S":
            inicio = (i, j)
        elif grid[i][j] == "T":
            fim = (i, j)

dist = [[-1] * m for _ in range(n)]
fila = deque([inicio])
dist[inicio[0]][inicio[1]] = 0

dirs = [(1, 0), (-1, 0), (0, 1), (0, -1)]

while fila:
    x, y = fila.popleft()
    for dx, dy in dirs:
        nx, ny = x + dx, y + dy
        if 0 <= nx < n and 0 <= ny < m:
            if grid[nx][ny] != "#" and dist[nx][ny] == -1:
                dist[nx][ny] = dist[x][y] + 1
                fila.append((nx, ny))

print(dist[fim[0]][fim[1]])
```

---

# 18. Componentes Secretas

## Ideia Principal

Queremos SCC: componentes fortemente conexas.

Usaremos Kosaraju:

1. DFS no grafo original para obter ordem de saida.
2. Inverter as arestas.
3. DFS no grafo invertido na ordem reversa.

## Explicacao Para Leigo

Em grafo direcionado, nao basta haver caminho de A para B.

Para estar no mesmo grupo, A precisa chegar em B e B precisa voltar para A.

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

def dfs2(v):
    vis[v] = True
    for u in gr[v]:
        if not vis[u]:
            dfs2(u)

for i in range(1, n + 1):
    if not vis[i]:
        dfs(i)

vis = [False] * (n + 1)
componentes = 0

for v in reversed(ordem):
    if not vis[v]:
        componentes += 1
        dfs2(v)

print(componentes)
```

---

# 19. Terreno Do Reino

## Ideia Principal

Usar a formula do cadarco para calcular o dobro da area.

## Explicacao Para Leigo

Pegamos cada ponto e o proximo.

Somamos:

```text
x_i * y_proximo - y_i * x_proximo
```

No final, o valor absoluto e o dobro da area.

## Complexidade

```text
O(N)
```

## Codigo Python

```python
n = int(input())
p = [tuple(map(int, input().split())) for _ in range(n)]

soma = 0

for i in range(n):
    x1, y1 = p[i]
    x2, y2 = p[(i + 1) % n]
    soma += x1 * y2 - y1 * x2

print(abs(soma))
```

---

# 20. Muralha Convexa

## Ideia Principal

Calcular o fecho convexo dos pontos.

O fecho convexo e como passar um elastico ao redor de todos os pontos.

Os pontos tocados pelo elastico ficam na borda.

## Explicacao Para Leigo

Pontos internos nao fazem parte da muralha.

Precisamos ordenar os pontos e construir a parte inferior e superior da casca.

## Complexidade

```text
O(N log N)
```

## Codigo Python

```python
def cross(o, a, b):
    return (a[0] - o[0]) * (b[1] - o[1]) - (a[1] - o[1]) * (b[0] - o[0])

def convex_hull(pontos):
    pontos = sorted(set(pontos))

    if len(pontos) <= 1:
        return pontos

    baixo = []
    for p in pontos:
        while len(baixo) >= 2 and cross(baixo[-2], baixo[-1], p) <= 0:
            baixo.pop()
        baixo.append(p)

    cima = []
    for p in reversed(pontos):
        while len(cima) >= 2 and cross(cima[-2], cima[-1], p) <= 0:
            cima.pop()
        cima.append(p)

    return baixo[:-1] + cima[:-1]

n = int(input())
pontos = [tuple(map(int, input().split())) for _ in range(n)]

casca = convex_hull(pontos)
print(len(casca))
```

---

# Observacao Final

Essas solucoes sao referencias didaticas.

Em treino de OBI, e importante que o aluno:

1. tente resolver antes de olhar o gabarito;
2. escreva a ideia em linguagem natural;
3. estime a complexidade;
4. implemente;
5. compare com a solucao comentada.

