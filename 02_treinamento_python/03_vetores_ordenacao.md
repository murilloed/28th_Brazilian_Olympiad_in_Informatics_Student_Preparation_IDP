# 03 - Listas E Ordenacao Simples Em Python

## Objetivo

Aprender a armazenar sequencias, percorrer listas, calcular estatisticas simples e ordenar valores.

Em Python, o equivalente mais comum ao vetor e a **lista**.

## Criando Uma Lista

```python
valores = [10, 20, 30]
```

## Lendo Uma Lista

```python
n = int(input())
valores = list(map(int, input().split()))
```

## Percorrendo Uma Lista

```python
for x in valores:
    print(x)
```

## Soma, Maior E Menor

```python
soma = sum(valores)
maior = max(valores)
menor = min(valores)
```

## Ordenando

```python
valores.sort()
```

ou:

```python
ordenados = sorted(valores)
```

## Contagem De Frequencia

```python
freq = [0] * 101

for x in valores:
    freq[x] += 1
```

## Exercicios

1. Leia `N` pontuacoes e imprima maior, menor e soma.
2. Leia `N` notas e conte quantas ficaram acima da media.
3. Leia `N`, `K` e as pontuacoes. Imprima a menor pontuacao entre os `K` melhores.
4. Leia codigos entre `0` e `100` e imprima o codigo mais frequente.

