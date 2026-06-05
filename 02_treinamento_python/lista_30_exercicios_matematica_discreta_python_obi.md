# Lista De 30 Exercicios - Matematica Discreta Em Python Para OBI

Lista baseada na aula:

```text
aula_matematica_discreta_python_obi.md
```

## Orientacoes

Para cada exercicio:

1. Leia o enunciado com calma.
2. Identifique o conceito matematico envolvido.
3. Escreva a ideia da solucao antes do codigo.
4. Implemente em Python.
5. Teste com os exemplos e crie pelo menos mais 2 testes.

---

# Parte 1 - Funcoes E Relacoes

## Exercicio 1 - Funcao Dobro Mais Um

Leia um inteiro `x` e calcule:

```text
f(x) = 2x + 1
```

### Entrada

```text
3
```

### Saida

```text
7
```

## Exercicio 2 - Valor Da Funcao

Leia dois inteiros `a` e `b`. Depois leia um inteiro `x`. Calcule:

```text
f(x) = ax + b
```

### Entrada

```text
2 5
4
```

### Saida

```text
13
```

## Exercicio 3 - Relacao De Divisibilidade

Leia dois inteiros `a` e `b`. Diga se `a` divide `b`.

### Entrada

```text
3 12
```

### Saida

```text
SIM
```

---

# Parte 2 - Ordem Lexicografica

## Exercicio 4 - Menor Palavra

Leia duas palavras e imprima a menor em ordem lexicografica.

### Entrada

```text
casa carro
```

### Saida

```text
carro
```

## Exercicio 5 - Ordenar Palavras

Leia `n` palavras e imprima todas em ordem lexicografica.

### Entrada

```text
4
banana
ana
casa
carro
```

### Saida

```text
ana
banana
carro
casa
```

---

# Parte 3 - Conjuntos

## Exercicio 6 - Elementos Unicos

Leia `n` inteiros e imprima quantos valores diferentes aparecem.

### Entrada

```text
6
1 2 2 3 3 3
```

### Saida

```text
3
```

## Exercicio 7 - Intersecao De Turmas

Duas turmas participaram de atividades. Leia os alunos da turma A e da turma B e informe quantos nomes aparecem nas duas turmas.

### Entrada

```text
3
ana bia caio
4
caio dan ana edu
```

### Saida

```text
2
```

## Exercicio 8 - Uniao De Conjuntos

Leia dois conjuntos de numeros e imprima a quantidade de elementos na uniao.

### Entrada

```text
3
1 2 3
3
3 4 5
```

### Saida

```text
5
```

---

# Parte 4 - Recursao

## Exercicio 9 - Fatorial Recursivo

Leia `n` e calcule `n!` usando recursao.

### Entrada

```text
5
```

### Saida

```text
120
```

## Exercicio 10 - Soma Recursiva

Leia `n` e calcule:

```text
1 + 2 + 3 + ... + n
```

usando recursao.

### Entrada

```text
4
```

### Saida

```text
10
```

## Exercicio 11 - Potencia Recursiva

Leia `a` e `b`. Calcule:

```text
a^b
```

usando recursao.

### Entrada

```text
2 5
```

### Saida

```text
32
```

---

# Parte 5 - Permutacoes E Fatorial

## Exercicio 12 - Quantas Filas

Leia `n`, a quantidade de alunos. Calcule de quantas formas eles podem ser organizados em fila.

### Entrada

```text
4
```

### Saida

```text
24
```

## Exercicio 13 - Anagramas Sem Letras Repetidas

Leia uma palavra com todas as letras diferentes. Imprima quantos anagramas podem ser formados.

### Entrada

```text
abc
```

### Saida

```text
6
```

---

# Parte 6 - Progressao Aritmetica

## Exercicio 14 - Termo Da PA

Leia `a1`, `r` e `n`. Calcule o termo `n` da progressao aritmetica.

### Entrada

```text
2 3 5
```

### Saida

```text
14
```

## Exercicio 15 - Soma Da PA

Leia `a1`, `r` e `n`. Calcule a soma dos `n` primeiros termos da PA.

Formula:

```text
S = n * (a1 + an) / 2
```

### Entrada

```text
2 3 5
```

### Saida

```text
40
```

---

# Parte 7 - Principio Da Casa Dos Pombos

## Exercicio 16 - Mesmo Mes

Leia o numero de pessoas `n`. Diga se e garantido que duas pessoas nasceram no mesmo mes.

Considere 12 meses.

### Entrada

```text
13
```

### Saida

```text
SIM
```

## Exercicio 17 - Gavetas E Meias

Ha `c` cores de meias. Leia `c`. Qual e o menor numero de meias que precisam ser retiradas para garantir duas da mesma cor?

### Entrada

```text
5
```

### Saida

```text
6
```

---

# Parte 8 - Principio Aditivo E Multiplicativo

## Exercicio 18 - Escolha Do Lanche

Leia `s`, quantidade de salgados, e `d`, quantidade de doces. Se o aluno escolher salgado ou doce, quantas opcoes existem?

### Entrada

```text
3 2
```

### Saida

```text
5
```

## Exercicio 19 - Uniforme Completo

Leia a quantidade de camisetas, calcas e tenis. Calcule quantos uniformes completos diferentes podem ser montados.

### Entrada

```text
3 2 4
```

### Saida

```text
24
```

## Exercicio 20 - Senhas Numericas

Uma senha tem `n` digitos. Cada digito pode ser de 0 a 9. Leia `n` e calcule quantas senhas existem.

### Entrada

```text
3
```

### Saida

```text
1000
```

---

# Parte 9 - Teoria Dos Jogos Basica

## Exercicio 21 - Jogo Das Pedras 1 Ou 2

Ha `n` pedras. Em cada jogada, o jogador pode tirar 1 ou 2 pedras. Quem tira a ultima vence.

Leia `n` e diga se a posicao inicial e vencedora ou perdedora.

### Entrada

```text
6
```

### Saida

```text
PERDEDORA
```

## Exercicio 22 - Jogo Das Pedras 1, 2 Ou 3

Ha `n` pedras. Em cada jogada, o jogador pode tirar 1, 2 ou 3 pedras. Quem tira a ultima vence.

Leia `n` e diga se a posicao inicial e vencedora ou perdedora.

### Entrada

```text
8
```

### Saida

```text
PERDEDORA
```

---

# Parte 10 - Progressao Geometrica

## Exercicio 23 - Termo Da PG

Leia `a1`, `q` e `n`. Calcule o termo `n` da progressao geometrica.

### Entrada

```text
2 3 4
```

### Saida

```text
54
```

## Exercicio 24 - Crescimento Duplicado

Uma bacteria dobra a cada hora. Leia a quantidade inicial `a` e o numero de horas `h`. Imprima a quantidade final.

### Entrada

```text
5 3
```

### Saida

```text
40
```

---

# Parte 11 - Combinacoes

## Exercicio 25 - Escolher Equipe

Leia `n` alunos e `k` vagas. Calcule de quantas formas e possivel escolher a equipe.

### Entrada

```text
5 2
```

### Saida

```text
10
```

## Exercicio 26 - Duplas

Leia `n`, o numero de alunos. Calcule quantas duplas diferentes podem ser formadas.

### Entrada

```text
6
```

### Saida

```text
15
```

---

# Parte 12 - Triangulo De Pascal

## Exercicio 27 - Linha Do Triangulo

Leia `n` e imprima a linha `n` do Triangulo de Pascal.

Considere a linha 0 como:

```text
1
```

### Entrada

```text
4
```

### Saida

```text
1 4 6 4 1
```

## Exercicio 28 - Valor C(n, k)

Leia `n` e `k`. Calcule `C(n, k)` usando a ideia do Triangulo de Pascal.

### Entrada

```text
5 2
```

### Saida

```text
10
```

---

# Parte 13 - Inclusao-Exclusao

## Exercicio 29 - Alunos Em Clubes

Em uma escola:

- `a` alunos gostam de Python;
- `b` alunos gostam de Java;
- `c` alunos gostam dos dois.

Leia `a`, `b` e `c`. Calcule quantos gostam de pelo menos uma das linguagens.

### Entrada

```text
10 8 3
```

### Saida

```text
15
```

## Exercicio 30 - Multiplos De 2 Ou 3

Leia `n`. Conte quantos numeros de 1 ate `n` sao multiplos de 2 ou de 3.

Use inclusao-exclusao.

### Entrada

```text
10
```

### Saida

```text
7
```

### Explicacao

Numeros de 1 ate 10 multiplos de 2:

```text
2, 4, 6, 8, 10
```

Multiplos de 3:

```text
3, 6, 9
```

Uniao:

```text
2, 3, 4, 6, 8, 9, 10
```

Total:

```text
7
```

---

# Desafio Final

Escolha 5 exercicios desta lista e, para cada um, entregue:

- conceito matematico usado;
- ideia da solucao;
- codigo em Python;
- 3 casos de teste;
- uma explicacao curta em linguagem natural.

