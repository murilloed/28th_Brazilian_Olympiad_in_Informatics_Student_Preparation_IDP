# 50 Erros Comuns Em Python Que Geram Erro Ou Resposta Errada

Este guia foi feito para treino de prova. Em competicoes como a OBI, muitas solucoes estao logicamente quase certas, mas falham por detalhes de entrada, saida, tipos, indices ou casos extremos.

## Top 50

1. Esquecer de converter `input()` para `int`.
2. Usar `a, b = int(input())` em vez de `a, b = map(int, input().split())`.
3. Imprimir texto extra que nao foi pedido.
4. Esquecer quebra de linha quando o formato pede uma resposta por linha.
5. Usar virgula na saida quando o problema pede espaco.
6. Esquecer `:` depois de `if`, `for`, `while`, `else`, `elif` ou `def`.
7. Errar a indentacao do bloco.
8. Misturar tab e espaco.
9. Usar `=` quando queria comparar com `==`.
10. Usar `==` quando queria atribuir com `=`.
11. Confundir `and` com `or`.
12. Esquecer que `range(n)` vai de `0` ate `n - 1`.
13. Usar `range(1, n)` quando precisava incluir `n`.
14. Acessar lista fora do limite.
15. Esquecer que o primeiro indice de uma lista e `0`.
16. Modificar uma lista enquanto percorre a mesma lista sem cuidado.
17. Achar que `sort()` retorna uma nova lista.
18. Usar `sorted(v)` sem guardar o retorno.
19. Comparar string numerica como se fosse numero.
20. Esquecer `.strip()` quando a string pode ter quebra de linha ou espacos.
21. Usar `input().split(" ")` quando ha multiplos espacos; prefira `split()`.
22. Nao tratar entrada com muitas linhas; em casos grandes, use `sys.stdin.read()`.
23. Esquecer de importar `sys` antes de usar `sys.stdin`.
24. Criar variavel com nome de funcao nativa, como `list`, `sum`, `max` ou `input`.
25. Usar divisao `/` quando precisava de divisao inteira `//`.
26. Esquecer que `%` calcula o resto.
27. Nao tratar divisor zero quando o enunciado permite.
28. Inicializar maior valor com `0` quando os numeros podem ser negativos.
29. Inicializar menor valor com `0` quando todos os numeros podem ser positivos.
30. Esquecer de atualizar contador dentro do laco.
31. Criar laco `while` sem alterar a condicao, causando loop infinito.
32. Usar `break` cedo demais.
33. Usar `continue` e pular uma atualizacao importante.
34. Confundir quantidade de elementos com soma dos elementos.
35. Ler `n`, mas nao usar `n` para controlar a quantidade de leituras.
36. Assumir que todos os valores virao em uma unica linha quando podem vir em varias.
37. Assumir que cada valor vira em uma linha quando podem vir na mesma linha.
38. Usar letras maiusculas/minusculas diferentes das exigidas na saida.
39. Imprimir acentos quando o enunciado espera texto sem acento.
40. Usar `float` em problema que exige aritmetica inteira exata.
41. Arredondar errado valores reais.
42. Ignorar empates.
43. Ignorar caso com `n = 0`, quando permitido.
44. Ignorar repeticoes de valores.
45. Esquecer de testar lista ja ordenada.
46. Esquecer de testar lista em ordem inversa.
47. Esquecer de testar menor entrada possivel.
48. Esquecer de testar maior entrada possivel.
49. Resolver so o exemplo do enunciado, sem generalizar a regra.
50. Submeter sem reler a saida esperada.

## Exemplos Rapidos

### Conversao De Entrada

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

### Varios Inteiros Na Mesma Linha

```python
a, b, c = map(int, input().split())
print(a + b + c)
```

### Maior Valor Com Numeros Negativos

Errado:

```python
maior = 0
```

Correto:

```python
maior = v[0]
```

### Entrada Grande

```python
import sys

dados = list(map(int, sys.stdin.read().split()))
```

## Checklist Antes De Submeter

- [ ] A saida esta exatamente no formato pedido?
- [ ] Todas as entradas numericas foram convertidas?
- [ ] Os lacos percorrem a quantidade certa?
- [ ] Os indices de listas estao dentro do limite?
- [ ] O codigo trata empate, zero e extremos?
- [ ] O algoritmo funciona alem do exemplo?

