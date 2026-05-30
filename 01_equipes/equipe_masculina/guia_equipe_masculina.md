# Guia Da Equipe Masculina - OBI 2026

Instituição: Instituto Brasileiro de Ensino, Desenvolvimento e Pesquisa - IDP

Equipe: alunos do primeiro período universitário

Modalidade oficial: Programação - Nível Sênior

Código na planilha: `PS`

Ano Escola: `U1`

Site oficial da OBI: <https://olimpiada.ic.unicamp.br/>

## 1. Objetivo Do Guia

Este guia orienta a equipe masculina do IDP para a participação na OBI 2026.

Ele reúne:

- modalidade correta;
- regras principais;
- linguagem de treino;
- formato da prova;
- estratégia de preparação;
- responsabilidades dos alunos;
- responsabilidades do professor/coordenador.

## 2. Modalidade Da Equipe Masculina

Como os alunos estão no primeiro período universitário, a modalidade correta é:

```text
Modalidade: Programação
Nível: Sênior
Código: PS
Ano Escola: U1
```

Não deve ser usado `P1` ou `P2`, pois esses níveis são voltados ao Ensino Fundamental e Ensino Médio.

## 3. Integrantes

| Nome | Data de nascimento | Gênero | Nível | Ano Escola |
|---|---|---|---|---|
| MARCO ANTONIO RODRIGUES SIQUEIRA | 19/11/2007 | M | PS | U1 |
| FRANKLIN DOS SANTOS CUNHA | 26/10/2000 | M | PS | U1 |
| GABRIEL BIZERRA DE ARAÚJO | 27/10/2007 | M | PS | U1 |
| DAVI BRANDÃO CAVALLARI DE OLIVEIRA | 09/06/2007 | M | PS | U1 |
| GAEL CEREGATTI MURAD | 05/06/2008 | M | PS | U1 |
| RAFAEL DIAS PALOMINO DOS SANTOS | 15/04/2007 | M | PS | U1 |

Observação: o email do Rafael ainda precisa ser confirmado para facilitar envio de senha e acesso ao ambiente da OBI.

## 4. Como Será A Prova?

A prova da Modalidade Programação é composta por tarefas de programação.

Cada tarefa apresenta:

- um enunciado;
- dados de entrada;
- dados de saída;
- exemplos;
- limites;
- uma regra ou situação a ser resolvida por código.

O aluno deve escrever um programa que leia os dados, processe corretamente e imprima a resposta esperada.

## 5. A Prova É Individual

A prova é individual.

Durante a aplicação oficial:

- não é permitido resolver em grupo;
- não é permitido conversar;
- não é permitido trocar código;
- não é permitido pedir ajuda ao professor;
- não é permitido usar internet fora do ambiente autorizado;
- não é permitido comentar o conteúdo da prova durante o dia de aplicação.

O treino pode ser em grupo. A prova não.

## 6. Linguagens Permitidas

Na Modalidade Programação, as linguagens permitidas são:

- C
- C++
- Java
- Python

Para esta equipe, o treinamento será focado em:

```text
C
```

## 7. Por Que Treinar Em C?

C é uma boa escolha porque:

- os alunos já estudam C;
- C é aceito oficialmente na OBI;
- ajuda a desenvolver raciocínio lógico;
- é rápido;
- obriga atenção com entrada, saída, vetores, índices e tipos;
- prepara bem para problemas de programação competitiva.

Ponto de atenção:

> Em C, pequenos erros de sintaxe, leitura ou índice de vetor podem derrubar uma solução correta.

## 8. Estrutura Básica Em C

```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);

    printf("%d\n", n);

    return 0;
}
```

## 9. Estrutura Básica Com Vetor

```c
#include <stdio.h>

int main() {
    int n;
    int v[1000];

    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        scanf("%d", &v[i]);
    }

    int soma = 0;
    for (int i = 0; i < n; i++) {
        soma += v[i];
    }

    printf("%d\n", soma);

    return 0;
}
```

## 10. Conteúdos Prioritários

A equipe deve dominar:

- entrada e saída com `scanf` e `printf`;
- variáveis;
- operadores;
- `if` e `else`;
- `for`;
- `while`;
- vetores;
- strings básicas;
- funções simples;
- maior e menor;
- soma e média;
- contadores;
- ordenação simples;
- busca linear;
- frequência;
- simulação de regras;
- leitura cuidadosa de enunciado.

## 11. Conteúdos Extras Se Houver Tempo

- matriz;
- busca binária;
- ordenação com critério;
- prefix sum;
- filas e pilhas simples;
- problemas de grafos básicos.

## 12. O Que Evitar Agora

Como o tempo é curto, não priorizar:

- segment tree;
- árvore Fenwick;
- programação dinâmica avançada;
- grafos complexos;
- geometria computacional;
- algoritmos muito avançados;
- teoria longa sem prática.

## 13. Estratégia De Prova

Durante a prova, o aluno deve:

1. Ler todos os problemas rapidamente.
2. Identificar o problema mais fácil.
3. Resolver primeiro o mais simples.
4. Testar com os exemplos.
5. Criar testes próprios.
6. Conferir formato de saída.
7. Submeter.
8. Evitar ficar preso muito tempo em um único problema.
9. Buscar pontuação parcial se não souber resolver tudo.

## 14. Como Ler Um Enunciado

Marcar:

- o que entra;
- o que sai;
- quais são as restrições;
- se há uma ou várias linhas;
- se precisa repetir até EOF;
- se os números cabem em `int` ou precisam de `long long`;
- se a ordem importa;
- se há casos especiais.

Perguntas obrigatórias:

```text
Qual é a entrada?
Qual é a saída?
Qual é a regra?
Qual é o menor caso?
Qual é o maior caso?
Minha solução passa no tempo?
```

## 15. Links De Prática

Site oficial:

<https://olimpiada.ic.unicamp.br/>

Área de prática:

<https://olimpiada.ic.unicamp.br/pratique/>

Ordem recomendada:

1. Programação Nível 1
2. Programação Nível 2
3. Programação Nível Sênior antigo Universitário

## 16. Frase Final

> A OBI não mede apenas quem sabe programar comandos, mas quem consegue transformar um problema em uma solução lógica, correta e eficiente.


