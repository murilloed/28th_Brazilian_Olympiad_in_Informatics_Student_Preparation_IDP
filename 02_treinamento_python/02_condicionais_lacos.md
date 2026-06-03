# 02 - Condicionais E Lacos Em Python

## Objetivo

Aprender a tomar decisoes e repetir comandos em Python.

## Condicional `if`

```python
x = int(input())

if x >= 60:
    print("APROVADO")
else:
    print("REPROVADO")
```

## `if`, `elif` E `else`

```python
p = int(input())

if p >= 90:
    print("ouro")
elif p >= 75:
    print("prata")
elif p >= 60:
    print("bronze")
else:
    print("participacao")
```

## Laco `for`

Use quando souber quantas repeticoes serao feitas.

```python
n = int(input())

for i in range(n):
    print(i)
```

## Laco `while`

Use quando a repeticao depende de uma condicao.

```python
x = int(input())

while x > 0:
    print(x)
    x -= 1
```

## Contador

```python
n = int(input())
aprovados = 0

for _ in range(n):
    nota = int(input())
    if nota >= 60:
        aprovados += 1

print(aprovados)
```

## Exercicios

1. Leia uma nota e imprima a classificacao.
2. Leia `N` notas e conte quantas sao maiores ou iguais a 60.
3. Leia uma sequencia de `0` e `1` e encontre a maior sequencia consecutiva de `1`.

