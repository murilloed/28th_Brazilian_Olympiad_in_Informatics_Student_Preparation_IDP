# 06 - Erros Comuns Em Python Na OBI

Este guia resume erros que costumam gerar resposta errada, erro de execucao ou perda de tempo em provas de programacao.

## 1. Esquecer De Converter Entrada Para Inteiro

Errado:

```python
n = input()
print(n + 1)
```

Correto:

```python
n = int(input())
print(n + 1)
```

`input()` sempre retorna texto. Para fazer conta, converta com `int()` ou `float()`.

## 2. Ler Varios Numeros Sem `split`

Errado:

```python
a, b = int(input())
```

Correto:

```python
a, b = map(int, input().split())
```

## 3. Imprimir Texto Extra

Errado:

```python
print("A resposta e", resposta)
```

Correto:

```python
print(resposta)
```

Em juiz online, normalmente a saida precisa ser exatamente a pedida.

## 4. Esquecer Dois-Pontos

Errado:

```python
if x > 0
    print("positivo")
```

Correto:

```python
if x > 0:
    print("positivo")
```

## 5. Errar Indentacao

Errado:

```python
if x > 0:
print("positivo")
```

Correto:

```python
if x > 0:
    print("positivo")
```

Python usa indentacao para definir blocos.

## 6. Confundir `=` Com `==`

Errado:

```python
if x = 10:
    print("igual")
```

Correto:

```python
if x == 10:
    print("igual")
```

`=` atribui valor. `==` compara.

## 7. Acessar Lista Fora Do Limite

Errado:

```python
v = [4, 7, 9]
print(v[3])
```

Correto:

```python
v = [4, 7, 9]
print(v[2])
```

O primeiro indice e `0`.

## 8. Confundir `sort()` E `sorted()`

```python
v = [3, 1, 2]
v.sort()
print(v)
```

`sort()` altera a lista original.

```python
v = [3, 1, 2]
ordenada = sorted(v)
print(ordenada)
```

`sorted()` cria uma nova lista ordenada.

## 9. Usar `input()` Em Entrada Muito Grande

Para muitas linhas, prefira:

```python
import sys

dados = sys.stdin.read().split()
```

Isso evita lentidao em problemas com muitos dados.

## 10. Nao Testar Casos Extremos

Sempre teste:

- menor entrada possivel;
- maior entrada possivel;
- empate;
- zero;
- valores repetidos;
- lista ja ordenada;
- lista em ordem inversa.

## Checklist Final

- [ ] Converteu entradas numericas com `int()`?
- [ ] Usou `split()` para varios valores na mesma linha?
- [ ] A saida esta sem texto extra?
- [ ] A indentacao esta correta?
- [ ] As listas respeitam indices de `0` a `n - 1`?
- [ ] Testou casos extremos?

