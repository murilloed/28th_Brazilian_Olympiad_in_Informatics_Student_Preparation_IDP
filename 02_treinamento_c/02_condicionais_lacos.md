# 02 - Condicionais E Laços Em C

## Objetivo

Usar decisões e repetições para resolver problemas.

Esses comandos são essenciais na OBI.

## Condicional `if`

```c
if (idade >= 18) {
    printf("maior\n");
} else {
    printf("menor\n");
}
```

## Comparadores

| Operador | Significado |
|---|---|
| `==` | igual |
| `!=` | diferente |
| `>` | maior |
| `<` | menor |
| `>=` | maior ou igual |
| `<=` | menor ou igual |

## Operadores Lógicos

| Operador | Significado |
|---|---|
| `&&` | e |
| `||` | ou |
| `!` | não |

Exemplo:

```c
if (nota >= 7 && faltas <= 10) {
    printf("aprovado\n");
}
```

## Laço `for`

Use quando souber quantas vezes repetir.

```c
for (int i = 0; i < 10; i++) {
    printf("%d\n", i);
}
```

## Laço `while`

Use quando a repetição depende de uma condição.

```c
int x;
scanf("%d", &x);

while (x != 0) {
    printf("%d\n", x);
    scanf("%d", &x);
}
```

## Contadores

Contar quantos números são pares:

```c
int n, x, pares = 0;
scanf("%d", &n);

for (int i = 0; i < n; i++) {
    scanf("%d", &x);
    if (x % 2 == 0) {
        pares++;
    }
}

printf("%d\n", pares);
```

## Acumuladores

Somar vários números:

```c
int n, x, soma = 0;
scanf("%d", &n);

for (int i = 0; i < n; i++) {
    scanf("%d", &x);
    soma += x;
}

printf("%d\n", soma);
```

## Erros Comuns

### Usar `=` no lugar de `==`

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

### Laço infinito

Errado:

```c
while (x > 0) {
    printf("%d\n", x);
}
```

Falta atualizar `x`.

## Exercício 1

Leia um inteiro e diga se ele é par ou ímpar.

## Exercício 2

Leia `N` números e conte quantos são positivos.

## Exercício 3

Leia `N` números e imprima a soma dos números pares.


