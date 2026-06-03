# Aula 03 E 04 - Listas, Ordenacao Simples E Strings Em Python

Material preparado para a equipe IDP na preparacao para a OBI 2026.

| Data | Carga | Tema |
|---|---:|---|
| 03/06 | 2h | Listas e ordenacao simples |
| 04/06 | 2h | Strings em Python |

## Objetivo Geral

Preparar os alunos para resolver problemas no estilo da OBI usando Python, com foco em armazenamento e manipulacao de sequencias:

- usar listas para guardar muitos valores;
- percorrer listas com `for`;
- encontrar maior, menor, soma e media;
- contar frequencias;
- ordenar valores com `sort()` e `sorted()`;
- entender busca simples;
- ler e manipular strings;
- comparar caracteres;
- contar letras, digitos e ocorrencias;
- evitar erros comuns com indices.

## Como A OBI Costuma Cobrar Esses Temas

Listas e strings aparecem quando o problema envolve uma colecao de dados:

- lista de notas;
- pontuacoes;
- cartas;
- alunos;
- posicoes;
- sequencias;
- palavras;
- codigos;
- placas;
- senhas;
- mensagens.

O aluno precisa perceber que nao basta ler um unico valor. Muitas vezes e necessario guardar varios valores e depois analisar a sequencia.

Exemplo:

```text
N valores foram informados.
Determine quantos sao maiores que a media.
```

Nesse caso, talvez seja necessario:

1. ler todos os valores;
2. guardar em uma lista;
3. calcular a media;
4. percorrer novamente para contar.

---

# Encontro 03 - Listas E Ordenacao Simples

## Roteiro De 2 Horas

| Tempo | Atividade |
|---:|---|
| 15 min | Revisao de lacos e contadores |
| 25 min | Explicacao de listas, indices e limites |
| 25 min | Exercicio 1 - soma, maior e menor |
| 25 min | Exercicio 2 - acima da media |
| 20 min | Ordenacao simples |
| 25 min | Exercicio dificil guiado |
| 5 min | Checklist de erros comuns |

## Conteudo Didatico

### O Que E Uma Lista

Lista e uma estrutura que guarda varios valores em uma unica variavel.

Exemplo:

```python
notas = [80, 40, 100, 60, 75]
```

As posicoes sao:

```text
notas[0] = 80
notas[1] = 40
notas[2] = 100
notas[3] = 60
notas[4] = 75
```

Em Python, o primeiro indice tambem e sempre `0`.

### Erro Classico

Se a lista tem tamanho 5, a ultima posicao e `4`, nao `5`.

Errado:

```python
notas = [80, 40, 100, 60, 75]
print(notas[5])
```

Correto:

```python
notas = [80, 40, 100, 60, 75]
print(notas[4])
```

### Lendo Uma Lista

Quando os valores estao na mesma linha:

```python
n = int(input())
v = list(map(int, input().split()))
```

Explicacao linha por linha:

- `n = int(input())` le a quantidade de valores;
- `input().split()` quebra a linha em varias partes;
- `map(int, ...)` converte cada parte para inteiro;
- `list(...)` transforma o resultado em uma lista.

### Percorrendo Uma Lista Pelo Valor

```python
for x in v:
    print(x)
```

Esse formato e bom quando voce so precisa do valor.

### Percorrendo Uma Lista Pelo Indice

```python
for i in range(n):
    print(v[i])
```

Esse formato e util quando voce precisa saber a posicao.

### Quando Preciso Guardar Em Lista?

Nem sempre precisa guardar.

Se voce so precisa somar, pode fazer direto:

```python
soma += x
```

Mas se voce precisa usar os valores depois, precisa guardar.

Exemplo:

```text
calcular media
depois contar quantos valores ficaram acima da media
```

Nesse caso, precisa guardar os valores.

---

## Exercicio 1 - Melhor E Pior Pontuacao

### Enunciado

Em um treinamento, `N` alunos fizeram um simulado. Cada aluno recebeu uma pontuacao inteira.

Determine:

- a maior pontuacao;
- a menor pontuacao;
- a soma total das pontuacoes.

### Entrada

A primeira linha contem um inteiro `N`.

A segunda linha contem `N` inteiros, representando as pontuacoes.

### Saida

Imprima tres inteiros:

```text
maior menor soma
```

### Exemplo

Entrada:

```text
5
80 40 100 60 75
```

Saida:

```text
100 40 355
```

### Ideia Da Solucao

Precisamos percorrer todos os valores e atualizar:

- `maior`;
- `menor`;
- `soma`.

Em Python, tambem poderiamos usar `max(v)`, `min(v)` e `sum(v)`, mas e importante entender a logica manual.

### Solucao Comentada

```python
n = int(input())
v = list(map(int, input().split()))

maior = v[0]
menor = v[0]
soma = 0

for x in v:
    if x > maior:
        maior = x

    if x < menor:
        menor = x

    soma += x

print(maior, menor, soma)
```

### Explicacao Linha Por Linha

```python
n = int(input())
```

Le a quantidade de pontuacoes.

```python
v = list(map(int, input().split()))
```

Le as pontuacoes e guarda todas em uma lista.

```python
maior = v[0]
menor = v[0]
```

Inicializa maior e menor com um valor real da entrada. Isso evita erro quando os valores podem ser negativos.

```python
soma = 0
```

Cria um acumulador para somar as pontuacoes.

```python
for x in v:
```

Percorre cada pontuacao da lista.

```python
if x > maior:
    maior = x
```

Se a pontuacao atual for maior que a maior conhecida, atualiza.

```python
if x < menor:
    menor = x
```

Se a pontuacao atual for menor que a menor conhecida, atualiza.

```python
soma += x
```

Soma a pontuacao atual ao total.

```python
print(maior, menor, soma)
```

Imprime os tres valores separados por espaco.

### Versao Python Curta

```python
n = int(input())
v = list(map(int, input().split()))

print(max(v), min(v), sum(v))
```

Use a versao curta quando a turma ja entender a logica.

---

## Exercicio 2 - Acima Da Media

### Enunciado

Um professor registrou as notas de `N` alunos. Ele quer saber quantos alunos ficaram acima da media da turma.

Leia `N` e depois `N` notas inteiras. Imprima quantas notas sao maiores que a media.

### Entrada

A primeira linha contem `N`.

A segunda linha contem `N` inteiros.

### Saida

Um inteiro representando a quantidade de notas acima da media.

### Exemplo

Entrada:

```text
5
10 20 30 40 50
```

Saida:

```text
2
```

### Ideia Da Solucao

Aqui precisamos guardar os valores.

Por que?

Porque primeiro precisamos calcular a media e depois comparar cada nota com ela.

### Solucao Comentada

```python
n = int(input())
notas = list(map(int, input().split()))

soma = sum(notas)
media = soma / n

acima = 0

for nota in notas:
    if nota > media:
        acima += 1

print(acima)
```

### Explicacao Linha Por Linha

```python
notas = list(map(int, input().split()))
```

Guarda todas as notas, porque vamos precisar delas de novo depois de calcular a media.

```python
soma = sum(notas)
```

Calcula a soma de todos os elementos da lista.

```python
media = soma / n
```

Calcula a media. Em Python, `/` gera divisao real.

```python
acima = 0
```

Contador de notas acima da media.

```python
for nota in notas:
```

Percorre todas as notas novamente.

```python
if nota > media:
    acima += 1
```

Se a nota for maior que a media, aumenta o contador.

```python
print(acima)
```

Imprime a resposta.

---

## Conteudo Didatico - Ordenacao Simples

Ordenar significa colocar os valores em ordem.

Exemplo:

```text
5 2 9 1
```

Ordenado:

```text
1 2 5 9
```

Em Python, existem duas formas principais:

### `sort()`

Altera a propria lista.

```python
v = [5, 2, 9, 1]
v.sort()
print(v)
```

Saida:

```text
[1, 2, 5, 9]
```

### `sorted()`

Cria uma nova lista ordenada.

```python
v = [5, 2, 9, 1]
ordenada = sorted(v)
print(ordenada)
```

### Ordenacao Decrescente

```python
v.sort(reverse=True)
```

### Quando Ordenar Ajuda?

Ordenar ajuda quando precisamos:

- achar os menores;
- achar os maiores;
- comparar vizinhos;
- agrupar valores iguais;
- calcular mediana;
- simplificar uma decisao.

---

## Exercicio 3 - Dificil: Premiados Do Simulado

### Enunciado

Em um simulado, `N` alunos receberam pontuacoes. O professor quer premiar os `K` alunos com maiores pontuacoes.

Leia `N`, `K` e as `N` pontuacoes. Imprima a menor pontuacao entre os alunos premiados.

### Entrada

A primeira linha contem dois inteiros `N` e `K`.

A segunda linha contem `N` inteiros.

### Saida

Um inteiro: a menor pontuacao que ainda recebe premio.

### Exemplo

Entrada:

```text
6 3
50 80 70 100 60 90
```

Saida:

```text
80
```

### Solucao Comentada

```python
n, k = map(int, input().split())
v = list(map(int, input().split()))

v.sort()

resposta = v[n - k]

print(resposta)
```

### Explicacao Linha Por Linha

```python
n, k = map(int, input().split())
```

Le a quantidade de alunos e a quantidade de premiados.

```python
v = list(map(int, input().split()))
```

Le as pontuacoes.

```python
v.sort()
```

Ordena as pontuacoes em ordem crescente.

Depois de ordenar:

```text
indice: 0  1  2  3  4  5
valor: 50 60 70 80 90 100
```

Se `K = 3`, os premiados estao nas posicoes:

```text
3, 4, 5
```

A primeira dessas posicoes e:

```text
n - k = 6 - 3 = 3
```

Por isso:

```python
resposta = v[n - k]
```

### Erro Comum

Usar:

```python
v[k]
```

Isso estaria errado porque `k` conta a partir do inicio, nao do fim.

---

## Exercicio 4 - Muito Dificil: Frequencia Mais Alta

### Enunciado

Um sistema registrou `N` codigos de problemas resolvidos por alunos. Cada codigo e um numero inteiro entre `0` e `100`.

Determine qual codigo apareceu mais vezes.

Se houver empate, imprima o menor codigo empatado.

### Entrada

A primeira linha contem `N`.

A segunda linha contem `N` inteiros entre `0` e `100`.

### Saida

Um inteiro: o codigo mais frequente.

### Exemplo

Entrada:

```text
8
4 2 4 3 2 4 2 2
```

Saida:

```text
2
```

### Ideia Da Solucao

Como os codigos vao de `0` a `100`, podemos criar uma lista de frequencia com 101 posicoes.

### Solucao Comentada

```python
n = int(input())
codigos = list(map(int, input().split()))

freq = [0] * 101

for codigo in codigos:
    freq[codigo] += 1

melhor_codigo = 0
melhor_freq = 0

for codigo in range(101):
    if freq[codigo] > melhor_freq:
        melhor_freq = freq[codigo]
        melhor_codigo = codigo

print(melhor_codigo)
```

### Explicacao Linha Por Linha

```python
freq = [0] * 101
```

Cria uma lista com 101 zeros. A posicao `0` conta o codigo 0, a posicao `1` conta o codigo 1, e assim por diante.

```python
for codigo in codigos:
    freq[codigo] += 1
```

Para cada codigo lido, aumenta a frequencia correspondente.

```python
for codigo in range(101):
```

Percorre os codigos de 0 ate 100.

```python
if freq[codigo] > melhor_freq:
```

Atualiza apenas quando encontra uma frequencia maior. Se houver empate, nao troca. Como percorremos do menor para o maior, o menor codigo empatado permanece.

---

# Encontro 04 - Strings Em Python

## Roteiro De 2 Horas

| Tempo | Atividade |
|---:|---|
| 15 min | Revisao de listas |
| 25 min | O que e string em Python |
| 20 min | Leitura com `input()` e cuidados |
| 25 min | Exercicio 1 - contar caracteres |
| 25 min | Exercicio 2 - validar padrao |
| 25 min | Exercicio dificil guiado |
| 5 min | Checklist de erros comuns |

## Conteudo Didatico

### O Que E Uma String Em Python

String e uma sequencia de caracteres.

Exemplo:

```python
nome = "MARIA"
```

Posicoes:

```text
nome[0] = M
nome[1] = A
nome[2] = R
nome[3] = I
nome[4] = A
```

### Tamanho De Uma String

```python
s = "MARIA"
print(len(s))
```

`len(s)` retorna a quantidade de caracteres.

### Percorrendo Uma String

Pelo caractere:

```python
for c in s:
    print(c)
```

Pelo indice:

```python
for i in range(len(s)):
    print(s[i])
```

### Comparando Strings

Em Python, podemos comparar strings com `==`.

```python
if nome == "MARIA":
    print("igual")
```

### Cuidados Com Entrada

Use `.strip()` para remover espacos e quebras de linha nas pontas:

```python
s = input().strip()
```

---

## Exercicio 5 - Contar Vogais

### Enunciado

Leia uma palavra formada apenas por letras minusculas. Conte quantas vogais existem nela.

Considere vogais:

```text
a e i o u
```

### Exemplo

Entrada:

```text
programacao
```

Saida:

```text
5
```

### Solucao Comentada

```python
s = input().strip()
vogais = 0

for c in s:
    if c in "aeiou":
        vogais += 1

print(vogais)
```

### Explicacao Linha Por Linha

```python
s = input().strip()
```

Le a palavra.

```python
vogais = 0
```

Cria um contador.

```python
for c in s:
```

Percorre cada caractere da palavra.

```python
if c in "aeiou":
```

Verifica se o caractere esta no conjunto de vogais.

```python
vogais += 1
```

Conta mais uma vogal.

```python
print(vogais)
```

Mostra o total.

---

## Exercicio 6 - Codigo Valido

### Enunciado

Um codigo de prova e considerado valido se:

- possui exatamente 6 caracteres;
- os tres primeiros caracteres sao letras maiusculas;
- os tres ultimos caracteres sao digitos.

Leia uma string e diga se ela e valida.

### Exemplo 1

Entrada:

```text
OBI123
```

Saida:

```text
VALIDO
```

### Exemplo 2

Entrada:

```text
ObI123
```

Saida:

```text
INVALIDO
```

### Solucao Comentada

```python
s = input().strip()
valido = True

if len(s) != 6:
    valido = False

for i in range(3):
    if not ("A" <= s[i] <= "Z"):
        valido = False

for i in range(3, 6):
    if not ("0" <= s[i] <= "9"):
        valido = False

if valido:
    print("VALIDO")
else:
    print("INVALIDO")
```

### Observacao Importante

Esse codigo supoe que `s` tem 6 caracteres quando entra nos lacos. Para ficar mais seguro, podemos colocar os lacos dentro de um `else`.

### Versao Mais Segura

```python
s = input().strip()

if len(s) != 6:
    print("INVALIDO")
else:
    valido = True

    for i in range(3):
        if not ("A" <= s[i] <= "Z"):
            valido = False

    for i in range(3, 6):
        if not ("0" <= s[i] <= "9"):
            valido = False

    if valido:
        print("VALIDO")
    else:
        print("INVALIDO")
```

---

## Exercicio 7 - Dificil: Palavra Espelhada

### Enunciado

Uma palavra e espelhada se ela pode ser lida da mesma forma da esquerda para a direita e da direita para a esquerda.

Leia uma palavra e diga se ela e espelhada.

### Exemplo 1

Entrada:

```text
radar
```

Saida:

```text
SIM
```

### Exemplo 2

Entrada:

```text
prova
```

Saida:

```text
NAO
```

### Solucao Comentada

```python
s = input().strip()
espelhada = True

n = len(s)

for i in range(n // 2):
    if s[i] != s[n - 1 - i]:
        espelhada = False

if espelhada:
    print("SIM")
else:
    print("NAO")
```

### Explicacao Da Logica

Comparamos:

- primeiro com ultimo;
- segundo com penultimo;
- terceiro com antepenultimo;
- e assim por diante.

Nao precisa comparar o caractere central.

### Versao Python Curta

```python
s = input().strip()

if s == s[::-1]:
    print("SIM")
else:
    print("NAO")
```

`s[::-1]` cria a string invertida.

---

## Exercicio 8 - Muito Dificil: Frequencia De Letras

### Enunciado

Leia uma palavra formada apenas por letras minusculas. Determine qual letra aparece mais vezes.

Se houver empate, imprima a letra que aparece primeiro no alfabeto.

### Exemplo

Entrada:

```text
banana
```

Saida:

```text
a
```

### Solucao Comentada

```python
s = input().strip()
freq = [0] * 26

for c in s:
    indice = ord(c) - ord("a")
    freq[indice] += 1

melhor = 0

for i in range(1, 26):
    if freq[i] > freq[melhor]:
        melhor = i

letra = chr(ord("a") + melhor)
print(letra)
```

### Explicacao Linha Por Linha

```python
freq = [0] * 26
```

Cria uma posicao para cada letra de `a` ate `z`.

```python
indice = ord(c) - ord("a")
```

Transforma uma letra em indice:

```text
a -> 0
b -> 1
c -> 2
...
z -> 25
```

```python
if freq[i] > freq[melhor]:
```

Atualiza apenas quando encontra frequencia maior. Se empatar, nao troca, entao a menor letra alfabetica permanece.

---

# Checklist De Aprendizagem

Ao fim das duas aulas, o aluno deve conseguir:

- [ ] criar listas;
- [ ] ler `N` valores em uma lista;
- [ ] percorrer lista com `for`;
- [ ] acessar corretamente indices de `0` a `n - 1`;
- [ ] calcular soma, maior e menor;
- [ ] calcular media e comparar valores;
- [ ] ordenar valores com `sort()` e `sorted()`;
- [ ] usar lista de frequencia;
- [ ] ler string com `input().strip()`;
- [ ] usar `len()`;
- [ ] percorrer caracteres;
- [ ] comparar caracteres;
- [ ] validar padroes em string;
- [ ] identificar palindromos;
- [ ] contar frequencia de letras.

## Erros Comuns

- Acessar `v[n]` quando o ultimo indice e `v[n - 1]`.
- Esquecer de converter entrada numerica com `int`.
- Usar `input().split()` sem `map(int, ...)` quando precisa de numeros.
- Achar que `sort()` retorna uma nova lista.
- Usar `sorted(v)` e esquecer de guardar o retorno.
- Imprimir texto extra que o problema nao pediu.
- Usar `/` quando precisa de divisao inteira `//`.
- Usar `>=` quando o empate deveria manter o menor valor.
- Esquecer que strings tambem comecam no indice `0`.

## Tarefa Para Casa

Resolver ou refazer:

1. Melhor E Pior Pontuacao.
2. Acima Da Media.
3. Premiados Do Simulado.
4. Frequencia Mais Alta.
5. Contar Vogais.
6. Codigo Valido.
7. Palavra Espelhada.
8. Frequencia De Letras.

Para cada exercicio, o aluno deve entregar:

- codigo em Python;
- pelo menos 3 casos de teste;
- explicacao curta da ideia da solucao;
- apontar qual estrutura foi usada: lista, ordenacao ou string.

## Orientacao Final Para Os Alunos

Listas e strings sao a ponte entre problemas simples e problemas realmente competitivos. Quando voce aprende a guardar, percorrer, contar e comparar sequencias, muitos enunciados da OBI passam a ficar mais claros.
