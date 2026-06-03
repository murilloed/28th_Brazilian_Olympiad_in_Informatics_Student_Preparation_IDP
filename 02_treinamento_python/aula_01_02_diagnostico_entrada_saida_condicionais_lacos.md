# Aula 01 E 02 - Diagnostico, Entrada/Saida, Condicionais E Lacos Em Python

Material preparado para a equipe IDP na preparacao para a OBI 2026.

| Data | Carga | Tema |
|---|---:|---|
| 01/06 | 2h | Diagnostico + entrada e saida |
| 02/06 | 2h | Condicionais e lacos |

## Objetivo Geral

Preparar os alunos para resolver problemas no estilo da OBI usando Python, com foco nos fundamentos que mais aparecem nas primeiras questoes de programacao:

- interpretar enunciados;
- identificar entradas e saidas;
- usar `input()`, `split()`, `map()` e `print()`;
- trabalhar com inteiros, strings e listas simples;
- construir decisoes com `if`, `elif` e `else`;
- repetir instrucoes com `for` e `while`;
- testar casos pequenos antes de submeter.

## Como A OBI Costuma Cobrar Esses Temas

Na modalidade Programacao, a OBI apresenta uma situacao-problema. O aluno precisa transformar o texto em uma regra computacional.

O caminho recomendado e:

1. entender a historia do problema;
2. identificar a entrada;
3. identificar exatamente a saida;
4. criar a regra;
5. testar manualmente com exemplos pequenos;
6. escrever o codigo;
7. conferir casos extremos.

---

# Encontro 01 - Diagnostico + Entrada E Saida

## Roteiro De 2 Horas

| Tempo | Atividade |
|---:|---|
| 15 min | Apresentacao do formato da OBI e combinados de treino |
| 20 min | Revisao de entrada e saida em Python |
| 25 min | Exercicio diagnostico 1 |
| 25 min | Exercicio diagnostico 2 |
| 25 min | Exercicio dificil guiado |
| 10 min | Fechamento: erros comuns e tarefa curta |

## Entrada Em Python

Para ler uma linha:

```python
texto = input()
```

Para ler um inteiro:

```python
n = int(input())
```

Para ler dois inteiros na mesma linha:

```python
a, b = map(int, input().split())
```

Explicacao linha por linha:

- `input()` le uma linha da entrada;
- `.split()` quebra a linha em partes separadas por espaco;
- `map(int, ...)` converte cada parte para inteiro;
- `a, b = ...` guarda os dois valores nas variaveis.

## Saida Em Python

Para imprimir uma resposta:

```python
print(resposta)
```

Em problemas de juiz online, evite texto extra. Se o enunciado pede apenas um numero, imprima apenas o numero.

## Exercicio Diagnostico 1 - Soma Da Pontuacao

Leia tres inteiros `A`, `B` e `C`, representando pontos obtidos em tres tarefas. Imprima a soma total.

Entrada:

```text
10 20 30
```

Saida:

```text
60
```

Solucao:

```python
a, b, c = map(int, input().split())
total = a + b + c
print(total)
```

Explicacao:

- `a, b, c` recebem os tres valores;
- `total` guarda a soma;
- `print(total)` exibe exatamente a resposta.

## Exercicio Diagnostico 2 - Hora Final

Leia a hora inicial `H` e a duracao `D`. Imprima a hora final em um relogio de 24 horas.

Entrada:

```text
22 5
```

Saida:

```text
3
```

Solucao:

```python
h, d = map(int, input().split())
fim = (h + d) % 24
print(fim)
```

Logica:

- somamos hora inicial e duracao;
- `% 24` faz a volta do relogio;
- se passar de 23, retorna para 0.

## Exercicio Dificil Guiado - Garrafas E Caixas

Uma caixa comporta `K` garrafas. Dado o numero de garrafas `N`, informe:

- quantidade de caixas cheias;
- quantidade de garrafas que sobram;
- quantidade total de caixas necessarias.

Entrada:

```text
23 6
```

Saida:

```text
3 5 4
```

Solucao:

```python
n, k = map(int, input().split())

cheias = n // k
resto = n % k

if resto == 0:
    total = cheias
else:
    total = cheias + 1

print(cheias, resto, total)
```

Explicacao:

- `n // k` calcula quantas caixas completas cabem;
- `n % k` calcula a sobra;
- se nao ha sobra, o total e igual ao numero de caixas cheias;
- se ha sobra, precisa de uma caixa a mais.

---

# Encontro 02 - Condicionais E Lacos

## Roteiro De 2 Horas

| Tempo | Atividade |
|---:|---|
| 15 min | Revisao do encontro anterior |
| 20 min | Condicionais |
| 25 min | Lacos com `for` |
| 25 min | Lacos com `while` |
| 25 min | Problema guiado no estilo OBI |
| 10 min | Fechamento e checklist |

## Condicionais

```python
pontos = int(input())

if pontos >= 80:
    print("ouro")
elif pontos >= 60:
    print("prata")
elif pontos >= 40:
    print("bronze")
else:
    print("participacao")
```

Explicacao:

- o primeiro `if` testa a maior faixa;
- `elif` significa "senao, se";
- `else` cobre todos os casos restantes;
- a ordem importa: se testar `pontos >= 40` primeiro, quase todo mundo cairia em bronze.

## Laco Com `for`

Conte quantas notas sao maiores ou iguais a 60.

```python
n = int(input())
aprovados = 0

for _ in range(n):
    nota = int(input())

    if nota >= 60:
        aprovados += 1

print(aprovados)
```

Explicacao:

- `range(n)` repete o bloco `n` vezes;
- `_` indica que o indice nao sera usado;
- `aprovados += 1` soma um ao contador.

## Laco Com `while`

Leia numeros ate encontrar zero. Imprima a soma dos numeros lidos antes do zero.

```python
soma = 0
x = int(input())

while x != 0:
    soma += x
    x = int(input())

print(soma)
```

Explicacao:

- o `while` continua enquanto a condicao for verdadeira;
- dentro do laco, e obrigatorio ler um novo `x`;
- se esquecer essa atualizacao, o programa pode entrar em loop infinito.

## Problema Guiado - Maior Pontuacao

Leia `n` pontuacoes e imprima a maior.

Entrada:

```text
5
10
80
30
90
70
```

Saida:

```text
90
```

Solucao:

```python
n = int(input())
maior = int(input())

for _ in range(n - 1):
    x = int(input())

    if x > maior:
        maior = x

print(maior)
```

Por que a primeira leitura e separada?

Porque o maior valor inicial deve ser um valor real da entrada. Se usassemos `maior = 0`, o codigo poderia falhar quando todas as pontuacoes fossem negativas, caso o problema permitisse.

## Checklist Do Aluno

- [ ] Sei ler um inteiro com `int(input())`.
- [ ] Sei ler varios inteiros com `map(int, input().split())`.
- [ ] Sei imprimir sem texto extra.
- [ ] Sei usar `if`, `elif` e `else`.
- [ ] Sei repetir `n` vezes com `for`.
- [ ] Sei repetir enquanto uma condicao vale com `while`.
- [ ] Sei testar casos pequenos manualmente.

## Tarefa Para Casa

Resolver 5 problemas antigos da OBI na area de pratica:

- 2 problemas faceis de entrada e saida;
- 2 problemas com condicionais;
- 1 problema com laco e contador.

Link: <https://olimpiada.ic.unicamp.br/pratique/>

