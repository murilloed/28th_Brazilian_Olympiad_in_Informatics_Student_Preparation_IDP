# Guia da Equipe Masculina IDP - OBI 2026

Instituicao: Instituto Brasileiro de Ensino, Desenvolvimento e Pesquisa - IDP

Equipe: alunos do primeiro periodo universitario

Modalidade oficial: Programacao - Nivel Senior

Codigo na planilha: `PS`

Ano Escola: `U1`

Site oficial da OBI: https://olimpiada.ic.unicamp.br/

## 1. O que e a OBI?

A OBI, Olimpiada Brasileira de Informatica, e uma competicao nacional organizada pela Sociedade Brasileira de Computacao, com organizacao a cargo do Instituto de Computacao da Unicamp.

Ela tem como objetivo:

- estimular o interesse por Computacao;
- desenvolver raciocinio logico e computacional;
- propor desafios de programacao;
- identificar talentos em Ciencia da Computacao;
- incentivar alunos a seguirem carreiras em tecnologia.

Na modalidade Programacao, os participantes resolvem problemas usando computador e uma linguagem de programacao permitida.

## 2. Modalidade da equipe masculina

Para alunos do primeiro periodo universitario, a modalidade correta e:

```text
Modalidade: Programacao
Nivel: Senior
Codigo: PS
Ano Escola: U1
```

Essa modalidade e individual. Mesmo sendo uma equipe de treinamento, cada aluno compete sozinho.

## 3. Alunos cadastrados na equipe masculina

| Nome | Data de nascimento | Genero | Nivel | Ano Escola |
|---|---|---|---|---|
| MARCO ANTONIO RODRIGUES SIQUEIRA | 19/11/2007 | M | PS | U1 |
| FRANKLIN DOS SANTOS CUNHA | 26/10/2000 | M | PS | U1 |
| GABRIEL BIZERRA DE ARAUJO | 27/10/2007 | M | PS | U1 |
| DAVI BRANDAO CAVALLARI DE OLIVEIRA | 09/06/2007 | M | PS | U1 |
| GAEL CEREGATTI MURAD | 05/06/2008 | M | PS | U1 |
| RAFAEL DIAS PALOMINO DOS SANTOS | 15/04/2007 | M | PS | U1 |

Observacao: o email do Rafael ainda precisa ser confirmado para facilitar envio de senha e acesso ao ambiente da OBI.

## 4. Datas principais da OBI 2026

| Etapa | Data / prazo | Observacao |
|---|---|---|
| Cadastro da escola para Modalidade Programacao | ate 06/06/2026 | responsabilidade do Coordenador Local |
| Inscricao dos competidores | ate 08/06/2026, 18h | envio da planilha/sistema |
| Fase Local | 10 a 12/06/2026 | horario escolhido pela instituicao |
| Fase Estadual | 20 a 21/08/2026 | apenas classificados |
| Fase Nacional | 03/10/2026, 13h-18h | apenas classificados |

## 5. Como sera a prova?

A prova da modalidade Programacao e composta por tarefas de programacao.

O aluno recebe problemas com uma historia, uma entrada e uma saida esperada. Ele deve implementar um programa que leia os dados, processe corretamente e imprima a resposta.

Caracteristicas:

- prova individual;
- feita no computador;
- presencial na instituicao na Fase Local;
- sem ajuda do professor durante a resolucao;
- sem acesso livre a internet;
- as solucoes sao submetidas em ambiente de prova;
- a correcao e feita por testes automaticos;
- cada tarefa pode valer ate 100 pontos.

## 6. E em grupo ou individual?

A prova e individual.

Isso significa:

- cada aluno resolve sozinho;
- nao pode conversar sobre a prova durante a aplicacao;
- nao pode compartilhar codigo;
- nao pode receber dica de algoritmo;
- nao pode pedir ao professor para corrigir a solucao durante a prova.

O grupo existe para treino antes da prova. Na prova, cada um compete por conta propria.

## 7. O professor pode ajudar durante a prova?

Durante a prova, nao.

O professor pode:

- treinar antes;
- explicar conteudos;
- aplicar simulados;
- ensinar C;
- ensinar estrategias;
- preparar laboratorio;
- orientar sobre regras;
- garantir funcionamento dos computadores.

O professor nao pode:

- explicar enunciado individualmente de forma que ajude na solucao;
- indicar algoritmo;
- corrigir codigo;
- depurar erro;
- dizer se a logica esta correta;
- sugerir casos de teste especificos durante a prova.

Frase importante:

> Todo apoio acontece antes da prova. Durante a prova, o aluno resolve sozinho.

## 8. Linguagens permitidas

Na modalidade Programacao, a OBI permite:

- C;
- C++;
- Java;
- Python.

Como a equipe estuda C, o treino sera focado em C.

## 9. Por que treinar em C?

C e uma boa escolha para a equipe porque:

- os alunos ja estudam C;
- e uma linguagem permitida na OBI;
- treina bem logica, memoria, tipos e entrada/saida;
- e rapida;
- obriga o aluno a entender detalhes importantes de implementacao.

Ponto de atencao:

> Em C, pequenos erros de sintaxe, leitura ou indice de vetor podem derrubar uma solucao correta. Por isso, o treino deve incluir muitos testes.

## 10. Estrutura basica de um programa em C para OBI

```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);

    printf("%d\n", n);

    return 0;
}
```

## 11. Estrutura basica com vetor

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

## 12. Conteudos que a equipe precisa dominar

Prioridade maxima:

- entrada e saida com `scanf` e `printf`;
- variaveis;
- operadores;
- `if` e `else`;
- `for`;
- `while`;
- vetores;
- strings basicas;
- funcoes simples;
- maior e menor;
- soma e media;
- contadores;
- ordenacao simples;
- busca linear;
- frequencia;
- simulacao de regras;
- leitura cuidadosa de enunciado.

Se sobrar tempo:

- matriz;
- busca binaria;
- ordenacao com criterio;
- prefix sum;
- filas e pilhas simples;
- mapas simulados com vetor de frequencia;
- problemas de grafos muito basicos.

## 13. O que evitar estudar agora

Como o tempo e curto, nao priorizar:

- segment tree;
- arvore Fenwick;
- programacao dinamica avancada;
- grafos complexos;
- geometria computacional;
- algoritmos muito avancados;
- teoria longa sem pratica.

Neste momento, o objetivo e pontuar bem em problemas acessiveis.

## 14. Calendario de treino intensivo

| Data | Carga | Foco |
|---|---:|---|
| 01/06 | 2h | Diagnostico + entrada/saida |
| 02/06 | 2h | Condicionais e lacos |
| 03/06 | 2h | Vetores e ordenacao simples |
| 04/06 | 2h | Strings em C |
| 05/06 | 2h | Simulacao e matematica simples |
| 06/06 | 3h | Simulado curto: 2h de prova + 1h de correcao |
| 07/06 | 2h | Revisao e refazer problemas errados |
| 08/06 | 2h30 | Nivel 2 facil/medio |
| 09/06 | 3h | Simulado final: 2h de prova + 1h de correcao |
| 10-12/06 | 2h de prova | Aplicacao oficial, conforme horario escolhido |

## 15. Modelo dos dias normais de treino

Para dias de 2 horas:

```text
20 min - explicacao objetiva
70 min - resolucao individual
20 min - correcao coletiva
10 min - checklist de erros em C
```

Para o dia de 2h30:

```text
20 min - estrategia de prova
90 min - problemas Nivel 2 facil/medio
30 min - correcao
10 min - plano individual de melhoria
```

## 16. Modelo dos simulados

Para dias de 3 horas:

```text
2h - simulado individual
40 min - correcao dos problemas
20 min - discussao de estrategia e erros
```

Durante o simulado:

- nao conversar;
- nao consultar internet;
- testar com os exemplos;
- criar testes proprios;
- controlar tempo;
- tentar primeiro os problemas mais faceis.

## 17. Onde praticar

Site oficial da OBI:

https://olimpiada.ic.unicamp.br/

Area de pratica:

```text
Pratique -> Modalidade Programacao
```

Ordem recomendada:

1. Programacao Nivel 1;
2. Programacao Nivel 2;
3. Nivel Senior antigo Universitario.

Mesmo que a categoria oficial seja Senior, para treino rapido e melhor comecar por Nivel 1 e Nivel 2.

## 18. Estrategia para resolver a prova

Passo a passo:

1. Ler todos os problemas rapidamente.
2. Identificar o mais facil.
3. Resolver primeiro o problema mais facil.
4. Nao ficar preso mais de 20 minutos no mesmo erro.
5. Testar com os exemplos.
6. Criar testes pequenos.
7. Conferir formato de saida.
8. Submeter.
9. Voltar para problemas mais dificeis.

## 19. Como ler um enunciado da OBI

Ao ler um problema, marcar:

- o que entra;
- o que sai;
- quais sao as restricoes;
- se ha uma ou varias linhas;
- se precisa repetir ate EOF;
- se os numeros cabem em `int` ou precisam de `long long`;
- se a ordem importa;
- se ha casos especiais.

Perguntas obrigatorias:

```text
Qual e a entrada?
Qual e a saida?
Qual e a regra?
Qual e o menor caso?
Qual e o maior caso?
Minha solucao passa no tempo?
```

## 20. Erros comuns em C

### Esquecer `&` no `scanf`

Errado:

```c
scanf("%d", n);
```

Correto:

```c
scanf("%d", &n);
```

### Passar do limite do vetor

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

### Esquecer quebra de linha na saida

Recomendado:

```c
printf("%d\n", resposta);
```

### Usar `int` quando precisa de `long long`

Quando valores podem passar de aproximadamente 2 bilhoes, usar:

```c
long long x;
scanf("%lld", &x);
printf("%lld\n", x);
```

### Comparar string com `==`

Errado:

```c
if (nome == "MARIA")
```

Correto:

```c
#include <string.h>

if (strcmp(nome, "MARIA") == 0)
```

## 21. Checklist antes de submeter

Antes de enviar uma solucao:

- compilou sem erro?
- testou com os exemplos?
- criou pelo menos dois testes proprios?
- conferiu se a saida tem exatamente o formato pedido?
- verificou se nao passou do vetor?
- verificou se nao esqueceu `&` no `scanf`?
- verificou se precisa de `long long`?
- verificou casos extremos?

## 22. Como estudar em casa

Cada aluno deve:

1. resolver pelo menos 2 problemas por dia;
2. anotar erros cometidos;
3. refazer problemas que errou;
4. guardar codigos de referencia;
5. treinar sem olhar solucao pronta;
6. tentar explicar a propria logica em voz alta.

## 23. O que e uma boa pontuacao?

Na OBI, muitas vezes nao e necessario resolver tudo para ir bem.

E melhor:

- resolver 1 problema com seguranca;
- tentar partes de outro;
- submeter solucoes parciais corretas;
- evitar erro bobo.

Lembrete:

> Uma solucao simples que passa em parte dos testes pode valer pontos. Uma solucao complexa errada pode valer zero.

## 24. Conduta durante a prova

Durante a prova:

- trabalhar sozinho;
- nao conversar;
- nao usar internet fora do ambiente permitido;
- nao copiar codigo de colegas;
- nao pedir ajuda na resolucao;
- nao comentar conteudo da prova com outras pessoas durante o dia;
- respeitar horario definido;
- manter documento e acesso organizados.

## 25. Responsabilidades do professor/coordenador

O professor/coordenador deve:

- confirmar cadastro do IDP;
- enviar inscricoes no prazo;
- garantir laboratorio/computadores;
- orientar antes da prova;
- aplicar a prova corretamente;
- garantir sigilo;
- acompanhar resultados;
- comunicar classificados;
- organizar proximas fases, se houver classificados.

## 26. Links importantes

Site oficial:

https://olimpiada.ic.unicamp.br/

Area de pratica:

https://olimpiada.ic.unicamp.br/pratique/

Calendario:

https://olimpiada.ic.unicamp.br/calendario/

Regulamento:

https://olimpiada.ic.unicamp.br/info/regulamento/

## 27. Resumo para os alunos

```text
Vocês participarão da OBI 2026 na Modalidade Programação - Nível Sênior.

A prova é individual, no computador, presencial no IDP na Fase Local.

Linguagem de treino: C.

Fase Local: 10 a 12/06/2026.

Duração: 2 horas.

Formato: problemas de programação com correção automática por testes.

Durante a prova, o professor não pode ajudar na resolução.

Todo treino e orientação acontecerá antes.
```

