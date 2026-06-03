# 01 - Entrada E Saida Em Python

## Objetivo

Aprender a ler dados de entrada e imprimir respostas no formato esperado pela OBI usando Python.

Em problemas de programacao, quase sempre o programa deve:

```text
ler dados
processar
imprimir resposta
```

## Estrutura Basica

```python
n = int(input())
print(n)
```

## Lendo Inteiros Na Mesma Linha

```python
a, b = map(int, input().split())
print(a + b)
```

Entrada:

```text
10 20
```

Saida:

```text
30
```

## Lendo Numeros Reais

```python
x = float(input())
print(f"{x:.2f}")
```

## Lendo Muitos Valores

```python
valores = list(map(int, input().split()))
```

## Lendo Ate O Fim Do Arquivo

```python
import sys

for linha in sys.stdin:
    x = int(linha)
    print(x)
```

## Saida Sem Texto Extra

Se o problema pede apenas:

```text
30
```

Nao faca:

```python
print("Resultado =", resposta)
```

Faca:

```python
print(resposta)
```

## Exercicios

1. Leia dois inteiros `A` e `B` e imprima a soma.
2. Leia tres inteiros e imprima o maior.
3. Leia um inteiro `N` e imprima o dobro.

