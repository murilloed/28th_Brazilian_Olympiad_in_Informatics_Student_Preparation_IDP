# 06 - Erros Comuns Em C

## Objetivo

Evitar erros simples que podem tirar pontos na OBI.

Em competição, muitas soluções erram não por falta de lógica, mas por detalhes de implementação.

## 1. Esquecer `&` No `scanf`

Errado:

```c
int n;
scanf("%d", n);
```

Correto:

```c
int n;
scanf("%d", &n);
```

## 2. Passar Do Limite Do Vetor

Errado:

```c
for (int i = 0; i <= n; i++) {
    scanf("%d", &v[i]);
}
```

Correto:

```c
for (int i = 0; i < n; i++) {
    scanf("%d", &v[i]);
}
```

## 3. Não Inicializar Variável

Errado:

```c
int soma;
soma += x;
```

Correto:

```c
int soma = 0;
soma += x;
```

## 4. Usar `=` Em Vez De `==`

Errado:

```c
if (x = 10) {
}
```

Correto:

```c
if (x == 10) {
}
```

## 5. Imprimir Texto Extra

Se a saída esperada é:

```text
42
```

Não imprimir:

```text
Resultado: 42
```

Em OBI, o formato da saída deve ser exatamente o pedido.

## 6. Esquecer `\n`

Recomendado:

```c
printf("%d\n", resposta);
```

## 7. Usar `int` Quando Precisa De `long long`

```c
long long x;
scanf("%lld", &x);
printf("%lld\n", x);
```

Use `long long` quando os valores podem passar de aproximadamente 2 bilhões.

## 8. Comparar Strings Com `==`

Errado:

```c
if (nome == "ANA")
```

Correto:

```c
#include <string.h>

if (strcmp(nome, "ANA") == 0) {
}
```

## 9. Misturar `scanf` E `fgets`

Depois de `scanf`, pode sobrar uma quebra de linha no buffer.

Solução comum:

```c
getchar();
fgets(texto, 100, stdin);
```

## 10. Esquecer Casos Extremos

Sempre testar:

- menor valor possível;
- maior valor possível;
- entrada com zero, se permitido;
- todos iguais;
- ordem crescente;
- ordem decrescente;
- apenas um elemento.

## Checklist Antes De Submeter

- O código compila?
- Testou com os exemplos?
- Testou caso pequeno?
- Testou caso extremo?
- A saída está exatamente igual ao pedido?
- Usou `&` no `scanf`?
- O vetor tem tamanho suficiente?
- O laço está com `< n` e não `<= n`?
- Precisa de `long long`?


