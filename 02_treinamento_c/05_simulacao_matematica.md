# 05 - Simulação E Matemática Simples

## Objetivo

Resolver problemas que exigem aplicar regras passo a passo.

Muitos problemas da OBI não pedem algoritmo avançado. Pedem atenção à regra.

## O Que É Simulação?

Simular é reproduzir no código o comportamento descrito no enunciado.

Exemplo:

```text
Um jogador ganha 3 pontos por vitória e 1 por empate.
Calcule a pontuação final.
```

Código:

```c
int vitorias, empates;
scanf("%d %d", &vitorias, &empates);

int pontos = vitorias * 3 + empates;
printf("%d\n", pontos);
```

## Matemática Básica Útil

### Resto Da Divisão

```c
if (n % 2 == 0) {
    printf("par\n");
}
```

### Divisão Inteira

```c
int x = 7 / 2; // resultado: 3
```

### Arredondamento Para Cima Em Inteiros

Para calcular quantos grupos de tamanho `k` são necessários para `n` itens:

```c
int grupos = (n + k - 1) / k;
```

## Problemas De Calendário

Muitas questões envolvem dias, horários e períodos.

Exemplo:

```c
int hora_inicio, hora_fim;
scanf("%d %d", &hora_inicio, &hora_fim);

int duracao;
if (hora_fim >= hora_inicio) {
    duracao = hora_fim - hora_inicio;
} else {
    duracao = 24 - hora_inicio + hora_fim;
}

printf("%d\n", duracao);
```

## Contagem De Casos

Exemplo: contar quantos alunos passaram.

```c
int n, nota, aprovados = 0;
scanf("%d", &n);

for (int i = 0; i < n; i++) {
    scanf("%d", &nota);
    if (nota >= 60) {
        aprovados++;
    }
}

printf("%d\n", aprovados);
```

## Estratégia Para Problemas De Simulação

1. Ler o enunciado devagar.
2. Identificar as regras.
3. Anotar exemplos pequenos.
4. Transformar cada regra em `if`, `for` ou cálculo.
5. Testar manualmente.

## Exercício 1

Leia vitórias e empates de um time. Imprima a pontuação.

## Exercício 2

Leia um número e diga se ele é múltiplo de 3 e de 5.

## Exercício 3

Leia horário inicial e final de um jogo e calcule a duração.


