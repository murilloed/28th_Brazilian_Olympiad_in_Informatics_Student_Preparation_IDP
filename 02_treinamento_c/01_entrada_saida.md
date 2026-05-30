# 01 - Entrada E Saída Em C

## Objetivo

Aprender a ler dados de entrada e imprimir respostas no formato esperado pela OBI.

Em problemas de programação, quase sempre o programa deve:

```text
ler dados
processar
imprimir resposta
```

## Estrutura Básica

```c
#include <stdio.h>

int main() {
    int n;

    scanf("%d", &n);
    printf("%d\n", n);

    return 0;
}
```

## Lendo Inteiros

```c
int a, b;
scanf("%d %d", &a, &b);
```

Exemplo de entrada:

```text
10 20
```

## Imprimindo Resultado

```c
printf("%d\n", a + b);
```

Sempre observe se o enunciado pede:

- uma resposta por linha;
- respostas separadas por espaço;
- texto específico;
- número inteiro;
- número com casas decimais.

## Lendo Números Reais

```c
double x;
scanf("%lf", &x);
printf("%.2f\n", x);
```

## Lendo Caracteres

```c
char c;
scanf(" %c", &c);
```

O espaço antes de `%c` ajuda a ignorar quebras de linha anteriores.

## Lendo Até O Fim Do Arquivo

Alguns problemas podem ter quantidade indefinida de entradas.

```c
int x;

while (scanf("%d", &x) != EOF) {
    printf("%d\n", x);
}
```

## Erros Comuns

### Esquecer `&`

Errado:

```c
scanf("%d", n);
```

Correto:

```c
scanf("%d", &n);
```

### Imprimir texto extra

Se o problema pede apenas o número:

```text
30
```

Não faça:

```c
printf("Resultado = %d\n", resposta);
```

Faça:

```c
printf("%d\n", resposta);
```

## Exercício 1

Leia dois inteiros `A` e `B` e imprima a soma.

Entrada:

```text
3 5
```

Saída:

```text
8
```

## Exercício 2

Leia três inteiros e imprima o maior.

## Exercício 3

Leia um número inteiro `N` e imprima o dobro dele.


