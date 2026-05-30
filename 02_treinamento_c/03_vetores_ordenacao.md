# 03 - Vetores E Ordenação Simples

## Objetivo

Aprender a armazenar vários valores e processá-los.

Vetores aparecem muito em problemas da OBI.

## Declarando Vetor

```c
int v[1000];
```

Esse vetor guarda até 1000 inteiros.

## Lendo Um Vetor

```c
int n, v[1000];
scanf("%d", &n);

for (int i = 0; i < n; i++) {
    scanf("%d", &v[i]);
}
```

## Percorrendo Um Vetor

```c
for (int i = 0; i < n; i++) {
    printf("%d\n", v[i]);
}
```

## Maior Valor

```c
int maior = v[0];

for (int i = 1; i < n; i++) {
    if (v[i] > maior) {
        maior = v[i];
    }
}

printf("%d\n", maior);
```

## Menor Valor

```c
int menor = v[0];

for (int i = 1; i < n; i++) {
    if (v[i] < menor) {
        menor = v[i];
    }
}
```

## Busca Linear

Verificar se um valor aparece:

```c
int procurado, achou = 0;
scanf("%d", &procurado);

for (int i = 0; i < n; i++) {
    if (v[i] == procurado) {
        achou = 1;
    }
}

if (achou) {
    printf("SIM\n");
} else {
    printf("NAO\n");
}
```

## Ordenação Simples

Para treino, use `qsort`.

```c
#include <stdio.h>
#include <stdlib.h>

int compara(const void *a, const void *b) {
    int x = *(int*)a;
    int y = *(int*)b;
    return x - y;
}

int main() {
    int n, v[1000];
    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        scanf("%d", &v[i]);
    }

    qsort(v, n, sizeof(int), compara);

    for (int i = 0; i < n; i++) {
        printf("%d\n", v[i]);
    }

    return 0;
}
```

## Frequência

Quando os valores são pequenos, podemos contar ocorrências.

```c
int freq[101] = {0};

for (int i = 0; i < n; i++) {
    freq[v[i]]++;
}
```

## Erros Comuns

### Passar Do Limite

Errado:

```c
for (int i = 0; i <= n; i++)
```

Correto:

```c
for (int i = 0; i < n; i++)
```

## Exercício 1

Leia `N` números e imprima o maior.

## Exercício 2

Leia `N` números e conte quantas vezes o número `X` aparece.

## Exercício 3

Leia `N` números e imprima-os em ordem crescente.


