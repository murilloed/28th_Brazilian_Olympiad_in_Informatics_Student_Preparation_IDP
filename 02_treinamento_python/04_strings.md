# 04 - Strings Em Python

## Objetivo

Aprender a ler, percorrer, comparar e analisar textos em Python.

## Lendo Uma String

```python
s = input().strip()
```

## Tamanho Da String

```python
n = len(s)
```

## Percorrendo Caracteres

```python
for ch in s:
    print(ch)
```

## Acessando Posicoes

```python
primeiro = s[0]
ultimo = s[-1]
```

## Contando Vogais

```python
s = input().strip()
vogais = 0

for ch in s:
    if ch in "aeiou":
        vogais += 1

print(vogais)
```

## Verificando Padrao

```python
s = input().strip()

if len(s) == 6 and s[:3].isupper() and s[3:].isdigit():
    print("VALIDO")
else:
    print("INVALIDO")
```

## Palavra Espelhada

```python
s = input().strip()

if s == s[::-1]:
    print("SIM")
else:
    print("NAO")
```

## Exercicios

1. Conte vogais.
2. Valide um codigo no formato `ABC123`.
3. Verifique se uma palavra e espelhada.
4. Encontre a letra minuscula mais frequente.

