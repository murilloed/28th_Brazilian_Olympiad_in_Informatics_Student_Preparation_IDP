# Modelos De Codigo Em Python Para OBI

Use estes modelos como ponto de partida. A ideia nao e decorar tudo, mas reconhecer rapidamente qual padrao combina com o problema.

## 1. Ler Um Inteiro

```python
n = int(input())
print(n)
```

## 2. Ler Dois Inteiros Na Mesma Linha

```python
a, b = map(int, input().split())
print(a + b)
```

## 3. Condicional

```python
x = int(input())

if x % 2 == 0:
    print("PAR")
else:
    print("IMPAR")
```

## 4. Repeticao Com `for`

```python
n = int(input())

for i in range(1, n + 1):
    print(i)
```

## 5. Ler Lista De Inteiros

```python
n = int(input())
v = list(map(int, input().split()))

for x in v:
    print(x)
```

## 6. Somar Valores De Uma Lista

```python
n = int(input())
v = list(map(int, input().split()))

soma = 0

for x in v:
    soma += x

print(soma)
```

## 7. Maior Valor

```python
n = int(input())
v = list(map(int, input().split()))

maior = v[0]

for x in v:
    if x > maior:
        maior = x

print(maior)
```

## 8. Ordenacao

```python
n = int(input())
v = list(map(int, input().split()))

v.sort()

for x in v:
    print(x)
```

## 9. String

```python
palavra = input().strip()
print(len(palavra))
```

## 10. Contar Caracteres

```python
texto = input().strip()
contador = 0

for caractere in texto:
    if caractere == "a":
        contador += 1

print(contador)
```

## 11. Entrada Rapida

```python
import sys

dados = sys.stdin.read().split()
indice = 0

n = int(dados[indice])
indice += 1

for _ in range(n):
    x = int(dados[indice])
    indice += 1
    print(x)
```

## 12. Funcao Para Organizar A Solucao

```python
def resolver():
    a, b = map(int, input().split())
    print(a + b)


resolver()
```

## 13. Padrao Recomendado Para Prova

```python
import sys


def resolver():
    entrada = sys.stdin.read().split()
    # Transforme a entrada de acordo com o enunciado.


if __name__ == "__main__":
    resolver()
```

