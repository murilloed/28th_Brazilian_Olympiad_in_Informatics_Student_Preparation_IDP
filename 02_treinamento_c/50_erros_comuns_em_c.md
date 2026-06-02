# 50 Erros Comuns Em C Que Geram Erro Ou Resposta Errada

Material de apoio para a preparacao da equipe IDP na OBI 2026.

Na OBI, muitos programas nao falham porque o aluno "nao sabia programar", mas porque deixou passar detalhes pequenos: um `&` esquecido, um `;` faltando, uma variavel nao inicializada ou uma saida diferente da esperada.

Este guia reune 50 erros frequentes em C, com exemplos e correcoes.

---

# 1. Esquecer `#include <stdio.h>`

## Erro

```c
int main() {
    printf("Oi\n");
    return 0;
}
```

## Correto

```c
#include <stdio.h>

int main() {
    printf("Oi\n");
    return 0;
}
```

## Comentario

`stdio.h` declara funcoes como `printf` e `scanf`.

---

# 2. Esquecer A Funcao `main`

## Erro

```c
printf("Oi\n");
```

## Correto

```c
#include <stdio.h>

int main() {
    printf("Oi\n");
    return 0;
}
```

## Comentario

O programa em C comeca pela funcao `main`.

---

# 3. Esquecer `return 0;`

## Erro

```c
int main() {
    printf("Fim\n");
}
```

## Correto

```c
int main() {
    printf("Fim\n");
    return 0;
}
```

## Comentario

Em compiladores modernos isso pode nao quebrar, mas `return 0;` indica encerramento correto.

---

# 4. Esquecer Ponto E Virgula

## Erro

```c
int x
scanf("%d", &x);
```

## Correto

```c
int x;
scanf("%d", &x);
```

## Comentario

Em C, quase toda instrucao termina com `;`.

---

# 5. Usar `=` No Lugar De `==`

## Erro

```c
if (x = 10) {
    printf("igual\n");
}
```

## Correto

```c
if (x == 10) {
    printf("igual\n");
}
```

## Comentario

`=` atribui valor. `==` compara.

---

# 6. Esquecer `&` No `scanf`

## Erro

```c
int x;
scanf("%d", x);
```

## Correto

```c
int x;
scanf("%d", &x);
```

## Comentario

O `scanf` precisa do endereco da variavel.

---

# 7. Usar Especificador Errado No `scanf`

## Erro

```c
double x;
scanf("%f", &x);
```

## Correto

```c
double x;
scanf("%lf", &x);
```

## Comentario

No `scanf`, `double` usa `%lf`.

---

# 8. Usar Especificador Errado No `printf`

## Erro

```c
long long x = 10000000000;
printf("%d\n", x);
```

## Correto

```c
long long x = 10000000000LL;
printf("%lld\n", x);
```

## Comentario

`long long` deve ser impresso com `%lld`.

---

# 9. Esquecer De Declarar Variavel

## Erro

```c
scanf("%d", &idade);
```

## Correto

```c
int idade;
scanf("%d", &idade);
```

## Comentario

Toda variavel precisa ser declarada antes de ser usada.

---

# 10. Escrever Nome De Variavel Diferente

## Erro

```c
int totalPontos = 0;
totalpontos = totalPontos + 10;
```

## Correto

```c
int totalPontos = 0;
totalPontos = totalPontos + 10;
```

## Comentario

C diferencia maiusculas de minusculas.

---

# 11. Nao Inicializar Contador

## Erro

```c
int cont;
cont++;
```

## Correto

```c
int cont = 0;
cont++;
```

## Comentario

Variavel local nao inicializada pode conter lixo de memoria.

---

# 12. Nao Inicializar Acumulador

## Erro

```c
int soma;
soma = soma + x;
```

## Correto

```c
int soma = 0;
soma = soma + x;
```

## Comentario

Acumuladores devem comecar com valor conhecido.

---

# 13. Esquecer Chaves Em Bloco Com Mais De Uma Linha

## Erro

```c
if (x > 0)
    printf("positivo\n");
    contador++;
```

## Correto

```c
if (x > 0) {
    printf("positivo\n");
    contador++;
}
```

## Comentario

Sem chaves, apenas a primeira linha pertence ao `if`.

---

# 14. Colocar Ponto E Virgula Depois Do `if`

## Erro

```c
if (x > 0);
{
    printf("positivo\n");
}
```

## Correto

```c
if (x > 0) {
    printf("positivo\n");
}
```

## Comentario

O `;` encerra o `if` antes do bloco.

---

# 15. Colocar Ponto E Virgula Depois Do `for`

## Erro

```c
for (int i = 0; i < n; i++);
{
    printf("%d\n", i);
}
```

## Correto

```c
for (int i = 0; i < n; i++) {
    printf("%d\n", i);
}
```

## Comentario

O `;` depois do `for` cria um laco vazio.

---

# 16. Loop Infinito Com `while`

## Erro

```c
int i = 0;
while (i < n) {
    printf("%d\n", i);
}
```

## Correto

```c
int i = 0;
while (i < n) {
    printf("%d\n", i);
    i++;
}
```

## Comentario

A variavel da condicao precisa mudar.

---

# 17. Erro De Limite No `for`

## Erro

```c
for (int i = 0; i <= n; i++) {
    printf("%d\n", v[i]);
}
```

## Correto

```c
for (int i = 0; i < n; i++) {
    printf("%d\n", v[i]);
}
```

## Comentario

Se o vetor tem `n` posicoes, os indices vao de `0` ate `n - 1`.

---

# 18. Acessar Posicao Inexistente Do Vetor

## Erro

```c
int v[10];
v[10] = 5;
```

## Correto

```c
int v[10];
v[9] = 5;
```

## Comentario

Em C, o primeiro indice e `0`.

---

# 19. Declarar Vetor Menor Que O Necessario

## Erro

```c
int v[100];
for (int i = 0; i < 1000; i++) {
    scanf("%d", &v[i]);
}
```

## Correto

```c
int v[1000];
for (int i = 0; i < 1000; i++) {
    scanf("%d", &v[i]);
}
```

## Comentario

Leia os limites do enunciado antes de declarar vetores.

---

# 20. Dividir Por Zero

## Erro

```c
media = soma / n;
```

## Correto

```c
if (n != 0) {
    media = soma / n;
}
```

## Comentario

Divisao por zero causa erro em tempo de execucao.

---

# 21. Usar Divisao Inteira Sem Perceber

## Erro

```c
int a = 5, b = 2;
double r = a / b;
```

## Correto

```c
int a = 5, b = 2;
double r = (double) a / b;
```

## Comentario

`5 / 2` com inteiros resulta em `2`, nao `2.5`.

---

# 22. Usar `int` Quando Precisa De `long long`

## Erro

```c
int produto = a * b;
```

## Correto

```c
long long produto = 1LL * a * b;
```

## Comentario

Produtos e somas grandes podem estourar `int`.

---

# 23. Esquecer `1LL` Em Produto Grande

## Erro

```c
long long ans = a * b;
```

## Correto

```c
long long ans = 1LL * a * b;
```

## Comentario

Se `a` e `b` forem `int`, o produto pode estourar antes de virar `long long`.

---

# 24. Imprimir Texto Extra

## Erro

```c
printf("Resposta: %d\n", x);
```

## Correto

```c
printf("%d\n", x);
```

## Comentario

Na OBI, imprima exatamente o que o enunciado pede.

---

# 25. Esquecer Quebra De Linha

## Erro

```c
printf("%d", x);
```

## Correto

```c
printf("%d\n", x);
```

## Comentario

Muitas vezes a falta de `\n` nao reprova, mas e melhor padronizar.

---

# 26. Colocar Espaco Extra Na Saida

## Erro

```c
printf("%d \n", x);
```

## Correto

```c
printf("%d\n", x);
```

## Comentario

Alguns juizes ignoram espacos extras, outros podem ser mais rigidos.

---

# 27. Nao Ler Todos Os Dados Da Entrada

## Erro

```c
scanf("%d", &n);
// esqueceu de ler os n valores
```

## Correto

```c
scanf("%d", &n);
for (int i = 0; i < n; i++) {
    scanf("%d", &x);
}
```

## Comentario

Se o enunciado informa `N` valores, o programa deve tratar todos.

---

# 28. Ler Dados Na Ordem Errada

## Erro

```c
scanf("%d %d", &b, &a);
```

## Correto

```c
scanf("%d %d", &a, &b);
```

## Comentario

A ordem de leitura deve seguir a ordem da entrada.

---

# 29. Confundir Linha Com Espaco Na Entrada

## Erro Conceitual

Achar que precisa de um `scanf` diferente porque os numeros estao em linhas separadas.

## Correto

```c
scanf("%d %d", &a, &b);
```

## Comentario

Para `scanf`, espaco, quebra de linha e tabulacao funcionam como separadores.

---

# 30. Usar `scanf("%c")` Depois De Ler Numero Sem Consumir Quebra De Linha

## Erro

```c
int n;
char c;
scanf("%d", &n);
scanf("%c", &c);
```

## Correto

```c
int n;
char c;
scanf("%d", &n);
scanf(" %c", &c);
```

## Comentario

O espaco antes de `%c` ignora quebras de linha e espacos pendentes.

---

# 31. Usar `gets`

## Erro

```c
char nome[100];
gets(nome);
```

## Correto

```c
char nome[100];
fgets(nome, 100, stdin);
```

## Comentario

`gets` e insegura e foi removida do padrao moderno da linguagem.

---

# 32. Esquecer O Tamanho Maximo Da String

## Erro

```c
char s[10];
scanf("%s", s);
```

## Correto

```c
char s[10];
scanf("%9s", s);
```

## Comentario

Uma string precisa de espaco para o caractere final `\0`.

---

# 33. Comparar Strings Com `==`

## Erro

```c
if (s == "SIM") {
    printf("ok\n");
}
```

## Correto

```c
#include <string.h>

if (strcmp(s, "SIM") == 0) {
    printf("ok\n");
}
```

## Comentario

Strings em C devem ser comparadas com `strcmp`.

---

# 34. Esquecer `#include <string.h>`

## Erro

```c
if (strcmp(a, b) == 0) {
    printf("iguais\n");
}
```

## Correto

```c
#include <string.h>

if (strcmp(a, b) == 0) {
    printf("iguais\n");
}
```

## Comentario

Funcoes de string ficam em `string.h`.

---

# 35. Nao Remover `\n` Do `fgets`

## Problema

`fgets` pode guardar a quebra de linha dentro da string.

## Correcao

```c
int len = strlen(s);
if (len > 0 && s[len - 1] == '\n') {
    s[len - 1] = '\0';
}
```

## Comentario

Isso afeta comparacoes com `strcmp`.

---

# 36. Usar Variavel Fora Do Escopo

## Erro

```c
for (int i = 0; i < n; i++) {
    printf("%d\n", i);
}
printf("%d\n", i);
```

## Correto

```c
int i;
for (i = 0; i < n; i++) {
    printf("%d\n", i);
}
printf("%d\n", i);
```

## Comentario

Se `i` foi declarada dentro do `for`, ela existe apenas dentro dele.

---

# 37. Esquecer Parenteses Em Condicao

## Erro

```c
if x > 0 {
    printf("positivo\n");
}
```

## Correto

```c
if (x > 0) {
    printf("positivo\n");
}
```

## Comentario

Condicoes de `if`, `while` e `for` usam parenteses.

---

# 38. Esquecer De Fechar Chaves

## Erro

```c
if (x > 0) {
    printf("positivo\n");
```

## Correto

```c
if (x > 0) {
    printf("positivo\n");
}
```

## Comentario

Quando o compilador acusa erro no final do arquivo, pode ser chave faltando.

---

# 39. Esquecer De Fechar Aspas

## Erro

```c
printf("Ola\n);
```

## Correto

```c
printf("Ola\n");
```

## Comentario

Strings precisam abrir e fechar aspas.

---

# 40. Usar Aspas Duplas Para Caractere

## Erro

```c
char c = "A";
```

## Correto

```c
char c = 'A';
```

## Comentario

Caractere usa aspas simples. String usa aspas duplas.

---

# 41. Usar Aspas Simples Para String

## Erro

```c
printf('Ola\n');
```

## Correto

```c
printf("Ola\n");
```

## Comentario

Texto em C usa aspas duplas.

---

# 42. Confundir `&&` Com `&`

## Erro

```c
if (a > 0 & b > 0) {
    printf("ok\n");
}
```

## Correto

```c
if (a > 0 && b > 0) {
    printf("ok\n");
}
```

## Comentario

`&&` e operador logico. `&` e operador bit a bit.

---

# 43. Confundir `||` Com `|`

## Erro

```c
if (a == 0 | b == 0) {
    printf("zero\n");
}
```

## Correto

```c
if (a == 0 || b == 0) {
    printf("zero\n");
}
```

## Comentario

`||` significa "ou" logico.

---

# 44. Esquecer Parenteses Em Expressao Logica

## Erro Possivel

```c
if (a > 0 && b > 0 || c > 0) {
    printf("ok\n");
}
```

## Melhor

```c
if ((a > 0 && b > 0) || c > 0) {
    printf("ok\n");
}
```

## Comentario

Parenteses deixam a intencao clara.

---

# 45. Usar `else` Sem `if`

## Erro

```c
if (x > 0) {
    printf("positivo\n");
}
else {
    printf("nao positivo\n");
}
else {
    printf("erro\n");
}
```

## Correto

```c
if (x > 0) {
    printf("positivo\n");
} else {
    printf("nao positivo\n");
}
```

## Comentario

Cada `else` precisa pertencer a um `if`.

---

# 46. Esquecer `else if` Em Cadeia De Decisao

## Erro

```c
if (nota >= 90) {
    printf("ouro\n");
}
if (nota >= 70) {
    printf("prata\n");
}
```

## Correto

```c
if (nota >= 90) {
    printf("ouro\n");
} else if (nota >= 70) {
    printf("prata\n");
}
```

## Comentario

Com varios `if`, mais de uma condicao pode executar.

---

# 47. Nao Tratar Empate Ou Igualdade

## Erro

```c
if (a > b) {
    printf("A\n");
} else {
    printf("B\n");
}
```

## Correto

```c
if (a > b) {
    printf("A\n");
} else if (b > a) {
    printf("B\n");
} else {
    printf("empate\n");
}
```

## Comentario

Se o problema permite empate, ele deve ser tratado.

---

# 48. Nao Testar O Menor Caso

## Erro Conceitual

Testar apenas casos grandes ou "normais".

## Correto

Sempre teste casos como:

```text
N = 1
N = 0, se permitido
todos iguais
todos zeros
```

## Comentario

Muitas respostas erradas aparecem nos limites pequenos.

---

# 49. Nao Testar O Maior Caso

## Erro Conceitual

Criar uma solucao que funciona para 10 valores, mas nao para 100000.

## Correto

Leia os limites e pense:

- o vetor cabe?
- a soma cabe em `int`?
- o algoritmo e rapido o suficiente?

## Comentario

Na OBI, parte dos testes escondidos verifica desempenho e limites.

---

# 50. Nao Fazer Teste De Mesa

## Erro Conceitual

Codificar direto sem simular manualmente.

## Correto

Antes de programar, simule pelo menos um exemplo:

```text
entrada -> variaveis -> processamento -> saida
```

## Comentario

Teste de mesa ajuda a encontrar erro de logica antes da submissao.

---

# Checklist Rapido Antes De Submeter

- [ ] Inclui `#include <stdio.h>`?
- [ ] O `main` esta correto?
- [ ] Todas as variaveis foram declaradas?
- [ ] Contadores e somas foram inicializados?
- [ ] Todo `scanf` tem `&`, exceto strings?
- [ ] Os formatos `%d`, `%lld`, `%lf` estao corretos?
- [ ] A saida esta exatamente como o enunciado pediu?
- [ ] Nao ha texto extra no `printf`?
- [ ] Os lacos param corretamente?
- [ ] Vetores nao acessam posicao fora do limite?
- [ ] Casos de empate foram tratados?
- [ ] Divisao por zero foi evitada?
- [ ] O programa foi testado com caso pequeno?
- [ ] O programa foi testado com caso limite?

