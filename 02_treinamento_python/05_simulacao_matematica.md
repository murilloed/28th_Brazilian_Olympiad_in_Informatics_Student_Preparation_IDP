# 05 - Simulacao E Matematica Simples Em Python

Este encontro prepara os alunos para problemas em que a dificuldade principal nao e uma formula pronta, mas sim entender a regra do enunciado e simular o processo com cuidado.

Na OBI, esse tipo de questao aparece muito em problemas de:

- placar;
- calendario;
- tempo;
- deslocamento;
- divisibilidade;
- contagem;
- pontuacao;
- regras de jogos;
- atualizacao de estados.

## 1. Ideia Central

Simular significa transformar a historia do problema em passos executaveis.

Exemplo:

> Um aluno ganha 3 pontos por vitoria e 1 ponto por empate. Dadas as quantidades de vitorias e empates, calcule a pontuacao.

```python
vitorias, empates = map(int, input().split())
pontos = vitorias * 3 + empates
print(pontos)
```

## 2. Par Ou Impar

```python
x = int(input())

if x % 2 == 0:
    print("par")
else:
    print("impar")
```

Explicacao:

- `%` calcula o resto da divisao;
- se o resto de `x / 2` for zero, o numero e par;
- caso contrario, e impar.

## 3. Duracao De Um Evento

Problema comum: o evento pode comecar em um dia e terminar no outro.

```python
inicio, fim = map(int, input().split())

if fim > inicio:
    duracao = fim - inicio
else:
    duracao = 24 - inicio + fim

print(duracao)
```

Exemplo:

Entrada:

```text
22 3
```

Saida:

```text
5
```

## 4. Contagem Com Regra

Leia `n` notas e conte quantas sao maiores ou iguais a 60.

```python
n = int(input())
aprovados = 0

for _ in range(n):
    nota = int(input())

    if nota >= 60:
        aprovados += 1

print(aprovados)
```

## 5. Divisibilidade

```python
a, b = map(int, input().split())

if a % b == 0:
    print("divisivel")
else:
    print("nao divisivel")
```

Cuidado: se `b` puder ser zero, o programa deve tratar esse caso antes da divisao.

## 6. Maximo, Minimo E Limites

Muitos problemas pedem para respeitar um limite.

Exemplo: uma bateria nao pode passar de 100 nem ficar abaixo de 0.

```python
energia, n = map(int, input().split())

for _ in range(n):
    variacao = int(input())
    energia += variacao

    if energia > 100:
        energia = 100
    elif energia < 0:
        energia = 0

print(energia)
```

## 7. Estrategia Para Problemas De Simulacao

Antes de programar:

1. Leia o enunciado inteiro.
2. Identifique quais valores mudam ao longo do tempo.
3. Defina as variaveis que representam o estado.
4. Simule manualmente um exemplo pequeno.
5. Escreva o codigo seguindo a mesma ordem da simulacao manual.
6. Teste com casos extremos.

## 8. Exercicios

### Exercicio 1 - Pontos Do Time

Leia vitorias, empates e derrotas. Cada vitoria vale 3 pontos, empate vale 1 e derrota vale 0. Imprima o total.

### Exercicio 2 - Relogio

Leia hora inicial e duracao em horas. Imprima a hora final em formato de 0 a 23.

### Exercicio 3 - Contador De Multiplos

Leia `n` numeros e conte quantos sao multiplos de 3.

### Exercicio 4 - Temperatura

Leia `n` temperaturas. Conte quantas ficaram acima de 30 graus.

### Exercicio 5 - Saldo

Leia saldo inicial e `n` movimentacoes. Cada movimentacao pode ser positiva ou negativa. Imprima o saldo final.

