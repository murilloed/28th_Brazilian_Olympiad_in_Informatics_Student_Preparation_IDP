# Aula 01 e 02 - Diagnostico, Entrada/Saida, Condicionais e Lacos

Material preparado para a equipe IDP na preparacao para a OBI 2026.

| Data | Carga | Tema |
|---|---:|---|
| 01/06 | 2h | Diagnostico + entrada e saida |
| 02/06 | 2h | Condicionais e lacos |

## Objetivo Geral

Preparar os alunos para resolver problemas no estilo da OBI usando linguagem C, com foco nos fundamentos que mais aparecem nas primeiras questoes de provas de programacao:

- interpretar enunciados;
- identificar entradas e saidas;
- usar `scanf` e `printf`;
- trabalhar com tipos numericos;
- construir decisoes com `if`, `else if` e `else`;
- repetir instrucoes com `for` e `while`;
- testar casos pequenos antes de submeter.

## Como A OBI Costuma Cobrar Esses Temas

Na modalidade Programacao, a OBI nao costuma pedir que o aluno "explique" o codigo. Ela apresenta uma situacao-problema. O aluno precisa:

1. entender a regra do problema;
2. descobrir quais dados serao recebidos;
3. produzir exatamente a saida pedida;
4. implementar uma solucao correta e eficiente;
5. passar nos testes escondidos.

Um erro comum de iniciante e achar que o problema e somente de sintaxe. Na OBI, a maior dificuldade geralmente esta em transformar texto em regra computacional.

---

# Encontro 01 - Diagnostico + Entrada E Saida

## Roteiro De 2 Horas

| Tempo | Atividade |
|---:|---|
| 15 min | Apresentacao do formato da OBI e combinados de treino |
| 20 min | Revisao rapida de entrada e saida em C |
| 25 min | Exercicio diagnostico 1 |
| 25 min | Exercicio diagnostico 2 |
| 25 min | Exercicio dificil guiado |
| 10 min | Fechamento: erros comuns e tarefa curta |

## Conteudo Didatico

### Entrada Em C

O comando principal para ler dados simples em C e o `scanf`.

Exemplo:

```c
int a, b;
scanf("%d %d", &a, &b);
```

Esse codigo le dois numeros inteiros.

Pontos importantes:

- `%d` le inteiro;
- `%lld` le `long long`;
- `%f` le `float`;
- `%lf` le `double`;
- o operador `&` indica o endereco da variavel;
- a entrada pode estar na mesma linha ou em linhas diferentes.

Para o `scanf`, estas entradas sao equivalentes:

```text
10 20
```

```text
10
20
```

### Saida Em C

O comando principal para imprimir dados e o `printf`.

```c
printf("%d\n", resposta);
```

Na OBI, a saida precisa bater exatamente com o esperado:

- cuidado com letras maiusculas e minusculas;
- cuidado com espacos extras;
- cuidado com quebras de linha;
- cuidado com acentos se o problema nao pedir.

## Exercicio 1 - Pontuacao Do Treino

### Enunciado

Em um treino da OBI, um aluno resolveu tres problemas. Cada problema vale uma quantidade diferente de pontos. O professor quer saber a pontuacao total do aluno.

Leia tres inteiros `A`, `B` e `C`, representando os pontos obtidos nos tres problemas. Imprima a soma total.

### Entrada

Tres inteiros `A`, `B` e `C`.

### Saida

Um unico inteiro, a soma dos tres valores.

### Exemplo

Entrada:

```text
30 50 20
```

Saida:

```text
100
```

### Ideia Da Solucao

Este e um problema de entrada, processamento e saida:

- entrada: ler `A`, `B` e `C`;
- processamento: somar os tres valores;
- saida: imprimir o resultado.

### Solucao Comentada

```c
#include <stdio.h>

int main() {
    int a, b, c;
    int total;

    scanf("%d %d %d", &a, &b, &c);

    total = a + b + c;

    printf("%d\n", total);

    return 0;
}
```

### Comentarios Para Explicar Em Aula

- `int a, b, c;` cria tres variaveis inteiras.
- `scanf("%d %d %d", &a, &b, &c);` le tres numeros.
- `total = a + b + c;` guarda a soma.
- `printf("%d\n", total);` imprime a resposta.

### Erros Comuns

- Esquecer o `&` no `scanf`.
- Imprimir texto junto com a resposta, por exemplo: `Total = 100`.
- Usar ponto e virgula errado.

---

## Exercicio 2 - Tempo Total De Prova

### Enunciado

Uma prova comeca em uma hora exata `H` e dura `D` horas. Sabendo que o relogio vai de 0 ate 23, determine em que hora a prova termina.

Se passar da meia-noite, a contagem deve voltar para 0.

### Entrada

Dois inteiros `H` e `D`.

### Saida

Um inteiro representando a hora de termino.

### Exemplo 1

Entrada:

```text
10 2
```

Saida:

```text
12
```

### Exemplo 2

Entrada:

```text
23 3
```

Saida:

```text
2
```

### Ideia Da Solucao

Se somarmos `H + D`, podemos passar de 23. Para voltar ao intervalo de 0 a 23, usamos o resto da divisao por 24.

Formula:

```text
fim = (H + D) % 24
```

### Solucao Comentada

```c
#include <stdio.h>

int main() {
    int h, d;
    int fim;

    scanf("%d %d", &h, &d);

    fim = (h + d) % 24;

    printf("%d\n", fim);

    return 0;
}
```

### Comentarios Para Explicar Em Aula

O operador `%` calcula o resto da divisao.

Exemplo:

```text
26 % 24 = 2
```

Por isso, se a prova comeca as 23h e dura 3h:

```text
23 + 3 = 26
26 % 24 = 2
```

A prova termina as 2h.

### Por Que Esse Problema E Estilo OBI

Ele parece simples, mas exige perceber uma regra de ciclo. Relogio, calendario, dias da semana e tabuleiros circulares aparecem bastante em problemas de programacao.

---

## Exercicio 3 - Dificil: Distribuicao De Salas

### Enunciado

Uma escola vai aplicar uma prova da OBI para `N` alunos. Cada sala comporta exatamente `K` alunos.

O coordenador quer saber:

- quantas salas completamente cheias serao usadas;
- se sera necessaria uma sala extra para os alunos restantes;
- o total de salas usadas.

### Entrada

Dois inteiros `N` e `K`.

### Saida

Tres inteiros:

1. quantidade de salas cheias;
2. quantidade de alunos na sala extra;
3. total de salas usadas.

Se nao houver sala extra, a quantidade de alunos na sala extra deve ser `0`.

### Exemplo 1

Entrada:

```text
53 20
```

Saida:

```text
2 13 3
```

### Exemplo 2

Entrada:

```text
60 20
```

Saida:

```text
3 0 3
```

### Ideia Da Solucao

Este problema usa divisao inteira e resto.

- `N / K` diz quantas salas cheias existem.
- `N % K` diz quantos alunos sobram.
- se sobrou algum aluno, precisamos de mais uma sala.

### Solucao Comentada

```c
#include <stdio.h>

int main() {
    int n, k;
    int cheias, resto, total;

    scanf("%d %d", &n, &k);

    cheias = n / k;
    resto = n % k;

    total = cheias;

    if (resto > 0) {
        total = total + 1;
    }

    printf("%d %d %d\n", cheias, resto, total);

    return 0;
}
```

### Comentarios Para Explicar Em Aula

Para `N = 53` e `K = 20`:

```text
53 / 20 = 2
53 % 20 = 13
```

Ou seja:

- 2 salas cheias;
- 13 alunos sobrando;
- precisa de mais 1 sala;
- total = 3 salas.

Para `N = 60` e `K = 20`:

```text
60 / 20 = 3
60 % 20 = 0
```

Ou seja:

- 3 salas cheias;
- nenhum aluno sobrando;
- total = 3 salas.

### Versao Mais Curta

Tambem poderiamos calcular o total assim:

```c
total = (n + k - 1) / k;
```

Mas para alunos iniciantes, a versao com `if` costuma ser mais didatica.

---

# Encontro 02 - Condicionais E Lacos

## Roteiro De 2 Horas

| Tempo | Atividade |
|---:|---|
| 15 min | Revisao da aula anterior |
| 20 min | Explicacao de condicionais |
| 20 min | Exercicio com `if` e `else` |
| 25 min | Explicacao de lacos |
| 30 min | Exercicio dificil com repeticao |
| 10 min | Fechamento e estrategia de prova |

## Conteudo Didatico

### Condicionais

Condicionais servem para o programa tomar decisoes.

```c
if (condicao) {
    // executa se a condicao for verdadeira
} else {
    // executa se a condicao for falsa
}
```

Operadores importantes:

| Operador | Significado |
|---|---|
| `==` | igual |
| `!=` | diferente |
| `>` | maior |
| `<` | menor |
| `>=` | maior ou igual |
| `<=` | menor ou igual |
| `&&` | e |
| `||` | ou |
| `!` | nao |

### Lacos

Lacos servem para repetir uma acao.

Use `for` quando souber quantas repeticoes tera:

```c
for (int i = 0; i < n; i++) {
    // repete n vezes
}
```

Use `while` quando a repeticao depender de uma condicao:

```c
while (condicao) {
    // repete enquanto a condicao for verdadeira
}
```

---

## Exercicio 4 - Classificacao De Desempenho

### Enunciado

Um aluno fez uma prova com pontuacao de 0 a 100. A classificacao e:

- `ouro`, se a pontuacao for maior ou igual a 90;
- `prata`, se for maior ou igual a 75 e menor que 90;
- `bronze`, se for maior ou igual a 60 e menor que 75;
- `participacao`, se for menor que 60.

Leia a pontuacao e imprima a classificacao.

### Entrada

Um inteiro `P`.

### Saida

Uma palavra:

- `ouro`
- `prata`
- `bronze`
- `participacao`

### Exemplo

Entrada:

```text
82
```

Saida:

```text
prata
```

### Solucao Comentada

```c
#include <stdio.h>

int main() {
    int p;

    scanf("%d", &p);

    if (p >= 90) {
        printf("ouro\n");
    } else if (p >= 75) {
        printf("prata\n");
    } else if (p >= 60) {
        printf("bronze\n");
    } else {
        printf("participacao\n");
    }

    return 0;
}
```

### Comentarios Para Explicar Em Aula

A ordem dos testes importa.

Quando o programa chega em:

```c
else if (p >= 75)
```

ele ja sabe que `p < 90`, porque se fosse `p >= 90`, teria entrado no primeiro `if`.

### Erro Comum

Fazer varios `if` separados:

```c
if (p >= 90) ...
if (p >= 75) ...
if (p >= 60) ...
```

Isso pode gerar mais de uma resposta para a mesma pontuacao.

---

## Exercicio 5 - Contagem De Aprovados

### Enunciado

Em um treino, `N` alunos fizeram um simulado. Cada aluno recebeu uma nota de 0 a 100.

Um aluno e considerado aprovado no treino se sua nota for maior ou igual a 60.

Leia `N` e depois as `N` notas. Imprima quantos alunos foram aprovados.

### Entrada

A primeira linha contem um inteiro `N`.

A segunda parte da entrada contem `N` inteiros, representando as notas.

### Saida

Um inteiro, a quantidade de aprovados.

### Exemplo

Entrada:

```text
5
80 40 60 59 100
```

Saida:

```text
3
```

### Ideia Da Solucao

Precisamos:

- ler `N`;
- repetir a leitura da nota `N` vezes;
- contar quantas notas sao maiores ou iguais a 60.

### Solucao Comentada

```c
#include <stdio.h>

int main() {
    int n;
    int nota;
    int aprovados = 0;

    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        scanf("%d", &nota);

        if (nota >= 60) {
            aprovados++;
        }
    }

    printf("%d\n", aprovados);

    return 0;
}
```

### Comentarios Para Explicar Em Aula

- `aprovados = 0` inicia o contador.
- O `for` repete exatamente `N` vezes.
- A cada nota lida, verificamos se ela e maior ou igual a 60.
- `aprovados++` significa `aprovados = aprovados + 1`.

### Teste De Mesa

Entrada:

```text
5
80 40 60 59 100
```

| Nota | Condicao `nota >= 60` | Aprovados |
|---:|---|---:|
| 80 | verdadeiro | 1 |
| 40 | falso | 1 |
| 60 | verdadeiro | 2 |
| 59 | falso | 2 |
| 100 | verdadeiro | 3 |

Resposta final: `3`.

---

## Exercicio 6 - Dificil: Maior Sequencia De Acertos

### Enunciado

Em um treinamento, um aluno resolveu uma sequencia de `N` problemas. Para cada problema, foi registrado:

- `1`, se ele acertou;
- `0`, se ele errou.

O professor quer descobrir qual foi a maior sequencia consecutiva de acertos desse aluno.

### Entrada

A primeira linha contem um inteiro `N`.

A segunda parte contem `N` inteiros, cada um sendo `0` ou `1`.

### Saida

Um inteiro representando a maior quantidade de acertos consecutivos.

### Exemplo 1

Entrada:

```text
8
1 1 0 1 1 1 0 1
```

Saida:

```text
3
```

### Exemplo 2

Entrada:

```text
5
0 0 0 0 0
```

Saida:

```text
0
```

### Ideia Da Solucao

Precisamos percorrer a sequencia e manter duas informacoes:

- `atual`: tamanho da sequencia atual de acertos;
- `maior`: maior sequencia encontrada ate agora.

Regras:

- se lemos `1`, aumentamos `atual`;
- se lemos `0`, zeramos `atual`;
- sempre que `atual` passar de `maior`, atualizamos `maior`.

### Solucao Comentada

```c
#include <stdio.h>

int main() {
    int n;
    int x;
    int atual = 0;
    int maior = 0;

    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        scanf("%d", &x);

        if (x == 1) {
            atual++;

            if (atual > maior) {
                maior = atual;
            }
        } else {
            atual = 0;
        }
    }

    printf("%d\n", maior);

    return 0;
}
```

### Comentarios Para Explicar Em Aula

Este problema e mais dificil porque nao basta contar quantos `1` existem. Precisamos contar os `1` consecutivos.

Na entrada:

```text
1 1 0 1 1 1 0 1
```

As sequencias de acertos sao:

```text
1 1       tamanho 2
1 1 1     tamanho 3
1         tamanho 1
```

A maior e `3`.

### Teste De Mesa

| Valor lido | Atual | Maior |
|---:|---:|---:|
| 1 | 1 | 1 |
| 1 | 2 | 2 |
| 0 | 0 | 2 |
| 1 | 1 | 2 |
| 1 | 2 | 2 |
| 1 | 3 | 3 |
| 0 | 0 | 3 |
| 1 | 1 | 3 |

Resposta: `3`.

---

## Exercicio 7 - Muito Dificil: Energia Do Robo

### Enunciado

Um robo participa de uma prova. Ele comeca com `E` pontos de energia.

Durante a prova, ele executa `N` acoes. Cada acao pode:

- consumir energia, representada por um numero negativo;
- recuperar energia, representada por um numero positivo.

O robo nunca pode ficar com energia menor que zero. Se em algum momento uma acao fizer a energia ficar negativa, o robo para imediatamente e a prova termina.

Leia a energia inicial `E`, a quantidade de acoes `N` e depois as `N` variacoes de energia.

Imprima:

- a energia final do robo;
- a quantidade de acoes executadas.

### Entrada

A primeira linha contem dois inteiros `E` e `N`.

A segunda parte contem `N` inteiros, representando as variacoes de energia.

### Saida

Dois inteiros:

```text
energia_final acoes_executadas
```

### Exemplo 1

Entrada:

```text
10 5
-3 -4 5 -2 -1
```

Saida:

```text
5 5
```

### Exemplo 2

Entrada:

```text
6 4
-2 -3 -5 10
```

Saida:

```text
1 2
```

### Explicacao Do Exemplo 2

Energia inicial: `6`

| Acao | Variacao | Energia apos acao | Executa? |
|---:|---:|---:|---|
| 1 | -2 | 4 | sim |
| 2 | -3 | 1 | sim |
| 3 | -5 | -4 | nao |
| 4 | 10 | nao chega nela | nao |

O robo para antes da terceira acao. Portanto:

- energia final: `1`;
- acoes executadas: `2`.

### Ideia Da Solucao

Para cada acao:

1. calcular quanto ficaria a energia;
2. se ficar negativa, parar;
3. caso contrario, confirmar a nova energia;
4. contar a acao executada.

### Solucao Comentada

```c
#include <stdio.h>

int main() {
    int e, n;
    int variacao;
    int executadas = 0;

    scanf("%d %d", &e, &n);

    for (int i = 0; i < n; i++) {
        scanf("%d", &variacao);

        if (e + variacao < 0) {
            break;
        }

        e = e + variacao;
        executadas++;
    }

    printf("%d %d\n", e, executadas);

    return 0;
}
```

### Comentarios Para Explicar Em Aula

O ponto central e perceber que nao podemos simplesmente somar tudo.

Exemplo:

```text
6 4
-2 -3 -5 10
```

Se somasse tudo:

```text
6 - 2 - 3 - 5 + 10 = 6
```

Mas isso estaria errado, porque o robo para antes de receber `+10`.

Esse tipo de problema aparece muito em competicoes: a ordem dos eventos importa.

### Variacao Para Desafio

Altere o problema para imprimir `OK` se o robo terminou todas as acoes e `FALHOU` se parou antes.

---

# Checklist De Aprendizagem

Ao fim das duas aulas, o aluno deve conseguir:

- [ ] ler um ou mais inteiros com `scanf`;
- [ ] imprimir exatamente a resposta pedida;
- [ ] usar divisao inteira e resto;
- [ ] construir decisoes com `if`, `else if` e `else`;
- [ ] repetir leituras com `for`;
- [ ] usar contador;
- [ ] usar acumulador;
- [ ] fazer teste de mesa;
- [ ] identificar casos especiais;
- [ ] explicar a ideia antes de codificar.

## Casos Especiais Para Treinar

Sempre pergunte:

- E se a entrada for o menor valor possivel?
- E se todos os valores forem iguais?
- E se nenhum aluno for aprovado?
- E se todos forem aprovados?
- E se a resposta for zero?
- E se a sequencia terminar no ultimo elemento?
- E se o programa precisar parar antes de ler tudo logicamente?

## Tarefa Para Casa

Resolver ou refazer:

1. Pontuacao Do Treino.
2. Tempo Total De Prova.
3. Distribuicao De Salas.
4. Contagem De Aprovados.
5. Maior Sequencia De Acertos.
6. Energia Do Robo.

Para cada exercicio, o aluno deve entregar:

- codigo em C;
- pelo menos 3 casos de teste;
- explicacao curta da ideia da solucao.

## Orientacao Final Para Os Alunos

Na OBI, nao ganha apenas quem sabe mais comandos. Ganha vantagem quem le melhor, testa melhor e erra menos nos detalhes.

