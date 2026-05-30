# Modelos De Código Em C Para OBI

## 1. Modelo Básico

```c
#include <stdio.h>

int main() {
    return 0;
}
```

## 2. Ler Um Inteiro

```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);
    printf("%d\n", n);
    return 0;
}
```

## 3. Ler Dois Inteiros E Somar

```c
#include <stdio.h>

int main() {
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d\n", a + b);
    return 0;
}
```

## 4. Condicional

```c
#include <stdio.h>

int main() {
    int x;
    scanf("%d", &x);

    if (x % 2 == 0) {
        printf("PAR\n");
    } else {
        printf("IMPAR\n");
    }

    return 0;
}
```

## 5. Laço Com `for`

```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        printf("%d\n", i);
    }

    return 0;
}
```

## 6. Vetor

```c
#include <stdio.h>

int main() {
    int n;
    int v[1000];

    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        scanf("%d", &v[i]);
    }

    for (int i = 0; i < n; i++) {
        printf("%d\n", v[i]);
    }

    return 0;
}
```

## 7. Maior Valor

```c
#include <stdio.h>

int main() {
    int n, v[1000];
    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        scanf("%d", &v[i]);
    }

    int maior = v[0];
    for (int i = 1; i < n; i++) {
        if (v[i] > maior) {
            maior = v[i];
        }
    }

    printf("%d\n", maior);

    return 0;
}
```

## 8. String

```c
#include <stdio.h>
#include <string.h>

int main() {
    char palavra[100];
    scanf("%s", palavra);

    printf("%d\n", (int)strlen(palavra));

    return 0;
}
```

## 9. Ordenação Com `qsort`

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

## 10. Ler Até EOF

```c
#include <stdio.h>

int main() {
    int x;

    while (scanf("%d", &x) != EOF) {
        printf("%d\n", x);
    }

    return 0;
}
```


