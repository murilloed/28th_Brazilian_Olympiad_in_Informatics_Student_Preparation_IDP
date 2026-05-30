# 04 - Strings Em C

## Objetivo

Aprender a ler, comparar e processar textos em C.

Strings em C são vetores de caracteres.

## Declarando String

```c
char nome[100];
```

## Lendo Uma Palavra

```c
scanf("%s", nome);
```

Isso lê até o primeiro espaço.

## Lendo Uma Linha Inteira

```c
fgets(nome, 100, stdin);
```

`fgets` pode guardar o `\n` no final da string.

## Biblioteca `string.h`

Use:

```c
#include <string.h>
```

Funções importantes:

| Função | Uso |
|---|---|
| `strlen` | tamanho da string |
| `strcmp` | comparar strings |
| `strcpy` | copiar string |
| `strcat` | concatenar |

## Tamanho Da String

```c
int tam = strlen(nome);
```

## Comparando Strings

Errado:

```c
if (nome == "MARIA")
```

Correto:

```c
if (strcmp(nome, "MARIA") == 0) {
    printf("igual\n");
}
```

## Percorrendo Caracteres

```c
for (int i = 0; nome[i] != '\0'; i++) {
    printf("%c\n", nome[i]);
}
```

## Contando Vogais

```c
int vogais = 0;

for (int i = 0; texto[i] != '\0'; i++) {
    char c = texto[i];
    if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
        vogais++;
    }
}
```

## Removendo Quebra De Linha Do `fgets`

```c
int tam = strlen(nome);
if (tam > 0 && nome[tam - 1] == '\n') {
    nome[tam - 1] = '\0';
}
```

## Erros Comuns

- Comparar string com `==`.
- Esquecer `#include <string.h>`.
- Usar vetor pequeno demais.
- Misturar `scanf` e `fgets` sem cuidado.
- Esquecer que string termina com `\0`.

## Exercício 1

Leia uma palavra e imprima seu tamanho.

## Exercício 2

Leia uma palavra e conte quantas letras `a` ela possui.

## Exercício 3

Leia duas palavras e diga se são iguais.


