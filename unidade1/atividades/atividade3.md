# Refinamento de prompts - Atividade

## 1. Identificação:

- **Disciplina:** Tendências em Ciência da Computação
- **Professora:** Kadidja Valéria Reginaldo de Oliveira
- **Integrante:** João Ricardo Barbosa Matos
- **Matrícula:** 33306109


## Problema escolhido

### Contexto

Estudantes do 1º semestre de Ciência da Computação estão aprendendo algoritmos de busca e ainda não dominam análise de complexidade. O material da disciplina introduz busca linear antes da busca binária, mas a transição entre as duas costuma gerar confusão sobre **quando** cada uma é adequada.

### Problema

Como explicar busca binária de forma intuitiva, sem depender de formalismo matemático, de modo que o estudante consiga **executar o algoritmo manualmente** e **reconhecer quando não usá-lo**?

### Objetivo

Obter uma explicação que permita ao estudante:

1. aplicar busca binária em um vetor ordenado;
2. identificar o pré-requisito de ordenação;
3. reconhecer situações em que a busca linear é mais adequada.

---

## Prompt 1

### Prompt

```text
Explique busca binária.
```

### Resultado

> A busca binária é um algoritmo de busca que opera em vetores ordenados, dividindo repetidamente o intervalo de busca pela metade. A cada iteração, compara-se o elemento central com o valor procurado: se forem iguais, a busca termina; se o valor procurado for menor, descarta-se a metade superior; se for maior, descarta-se a metade inferior. A complexidade de tempo é O(log n), o que a torna muito mais eficiente que a busca linear em grandes conjuntos de dados.

### Análise

- **O que funcionou?**
  - Definição tecnicamente correta.
  - Complexidade O(log n) mencionada corretamente.

- **O que faltou?**
  - Público-alvo não definido.
  - Nenhuma analogia ou intuição sobre *por que* dividir ao meio funciona.
  - Nenhum exemplo concreto passo a passo.
  - Pré-requisito de **vetor ordenado** não destacado.
  - Não mencionou quando a busca binária **não** é adequada.

- **O que ficou genérico?**
  - Complexidade citada sem justificativa intuitiva.

- **O que poderia ser melhor?**
  - Adicionar analogia cotidiana.
  - Incluir exemplo numérico passo a passo.
  - Explicitar o pré-requisito de ordenação.
  - Contrastar com busca linear.

- **O que precisa ser verificado?**
  - A afirmação "muito mais eficiente que a busca linear" é verdadeira apenas para vetores grandes; convém relativizar.

---

## Prompt 2

### Alterações realizadas

| Elemento | Alteração |
|---|---|
| Papel | professor de Ciência da Computação |
| Contexto | 1º semestre, sem análise de complexidade |
| Objetivo | compreensão intuitiva + aplicação prática |
| Público | iniciantes de graduação |
| Formato | definição → analogia → exemplo passo a passo → quando não usar |
| Restrições | sem fórmulas; máximo de 400 palavras |
| Critérios | aluno deve conseguir aplicar em um vetor simples |

### Prompt

```text
Atue como professor de Ciência da Computação.

Explique busca binária para estudantes do 1º semestre
que ainda não estudaram análise de complexidade.

Apresente:
1. definição simples;
2. analogia cotidiana;
3. exemplo passo a passo em um vetor ordenado;
4. uma situação em que busca binária NÃO deve ser usada.

Sem fórmulas matemáticas.
Máximo 400 palavras.
```

### Resultado

> **Definição simples**
> Busca binária é uma forma de procurar um valor em uma lista **ordenada** dividindo o espaço de busca pela metade a cada passo. Em vez de olhar item por item, o algoritmo "chuta" o meio e descarta metade da lista de uma vez.
>
> **Analogia cotidiana**
> Imagine procurar a palavra "manga" em um dicionário. Você não começa pela primeira página: abre o livro mais ou menos no meio, vê se está antes ou depois e descarta metade das páginas.
>
> **Exemplo passo a passo**
> Vetor ordenado: `[2, 5, 8, 12, 16, 23, 38]`. Procura-se o valor **23**.
> 1. Meio (índice 3): `12`. Como `12 < 23`, descarta-se a metade esquerda.
> 2. Intervalo `[16, 23, 38]`. Meio: `23`. Encontrado em 2 comparações.
>
> **Quando NÃO usar**
> - Vetor **não ordenado**.
> - Lista **muito pequena**.
> - Dados que mudam com frequência.

### Comparação P1 vs P2

| Critério | Prompt 1 | Prompt 2 |
|---|---:|---:|
| Clareza | 3 | 4 |
| Precisão | 4 | 4 |
| Relevância | 3 | 5 |
| Organização | 3 | 5 |
| Adequação ao público | 2 | 5 |
| Atendimento ao objetivo | 3 | 4 |
| Utilidade prática | 3 | 4 |
| **Total** | **21** | **31** |

**Escala:** 1 = muito insatisfatório · 2 = insatisfatório · 3 = adequado · 4 = muito bom · 5 = excelente

**Análise das melhorias:** O P2 ganhou em **adequação ao público** e **organização** por causa da estrutura explícita. A analogia tornou o conceito acessível. Porém, o exemplo passo a passo ainda não explicita o cálculo do índice do meio, e não há verificação de compreensão.

---

## Prompt 3

### O que ainda precisava melhorar?

- O exemplo passo a passo não explicita o cálculo do índice do meio.
- A analogia do dicionário é clichê.
- Não há **critério de qualidade** verificável.
- Não há **verificação de compreensão** ao final.
- Falta comparação estruturada entre busca binária e linear.

### Hipótese de melhoria

Acredito que a resposta ficará melhor porque explicitarei o **critério de qualidade** (o aluno deve executar manualmente a busca em um vetor de 8 posições), pedirei uma **analogia diferente** do dicionário, detalharei o **cálculo do índice do meio** e incluirei **perguntas de verificação** — forçando a IA a calibrar a profundidade e a produzir material autoavaliável.

### Prompt

```text
Atue como professor de Ciência da Computação especializado
em algoritmos.

CONTEXTO:
Estudantes do 1º semestre, sem base em análise de complexidade,
mas já sabem o que é um vetor.

OBJETIVO:
Que consigam executar busca binária manualmente em um vetor
de 8 posições e reconhecer quando NÃO usá-la.

TAREFA:
1. Definição em linguagem simples.
2. Analogia com situação cotidiana (não use dicionário).
3. Passo a passo detalhado, mostrando como calcular o índice do meio.
4. Dois casos em que busca binária não é adequada.
5. Uma tabela comparando busca binária e busca linear
   (critério, complexidade, pré-requisito).

FORMATO:
Subtítulos + tabela final.

RESTRIÇÕES:
- sem fórmulas;
- máximo de 450 palavras;
- explicar qualquer termo técnico utilizado.

CRITÉRIO DE QUALIDADE:
Ao final, o estudante deve conseguir executar manualmente
a busca pelo valor 12 no vetor [1, 3, 5, 7, 9, 11, 13, 15]
sem consultar a resposta.

Finalize com 2 perguntas para verificar a compreensão do estudante.
```

### Resultado

> **Definição simples**
> Busca binária encontra um valor em um vetor **ordenado** descartando metade dos elementos a cada comparação.
>
> **Analogia cotidiana**
> Adivinhar um número entre 1 e 100 com respostas "maior/menor". O melhor chute é **50**; depois **75** ou **25**; a cada tentativa, metade das possibilidades é eliminada.
>
> **Passo a passo detalhado**
> Vetor: `[1, 3, 5, 7, 9, 11, 13, 15]`. Procura-se **12**.
>
> 1. `esquerda = 0`, `direita = 7`. Meio: `(0+7)//2 = 3`. `vetor[3] = 7 < 12` → `esquerda = 4`.
> 2. `esquerda = 4`, `direita = 7`. Meio: `(4+7)//2 = 5`. `vetor[5] = 11 < 12` → `esquerda = 6`.
> 3. `esquerda = 6`, `direita = 7`. Meio: `(6+7)//2 = 6`. `vetor[6] = 13 > 12` → `direita = 5`.
> 4. `esquerda = 6 > direita = 5` → intervalo vazio. **12 não encontrado.**
>
> Foram 3 comparações; a busca linear faria 8.
>
> **Quando NÃO usar**
> - Vetor **desordenado**.
> - Listas **muito pequenas** ou que mudam com frequência.
>
> **Comparação: busca binária × busca linear**
>
> | Critério | Busca binária | Busca linear |
> |---|---|---|
> | Pré-requisito | Vetor ordenado | Nenhum |
> | Complexidade | O(log n) | O(n) |
> | Quando usar | Vetores grandes e ordenados | Vetores pequenos ou desordenados |
>
> **Verificação de compreensão**
> 1. Execute manualmente a busca pelo valor **12** no vetor `[1, 3, 5, 7, 9, 11, 13, 15]` e diga quantas comparações foram feitas.
> 2. Explique por que a busca binária **falha** em `[9, 3, 15, 1, 7, 11, 5, 13]`.

---

## Comparação final

| Critério | Prompt 1 | Prompt 2 | Prompt 3 |
|---|---:|---:|---:|
| Clareza | 3 | 4 | 5 |
| Precisão | 4 | 4 | 5 |
| Relevância | 3 | 5 | 5 |
| Organização | 3 | 5 | 5 |
| Adequação ao público | 2 | 5 | 5 |
| Atendimento ao objetivo | 3 | 4 | 5 |
| Utilidade prática | 3 | 4 | 5 |
| **Total** | **21** | **31** | **35** |

### Qual modificação teve maior impacto?

O **critério de qualidade** foi a modificação de maior impacto. Ao explicitar que "o estudante deve executar manualmente a busca pelo valor 12", a IA foi forçada a detalhar o cálculo do índice do meio, escolher um exemplo verificável e incluir perguntas de verificação. Em segundo lugar, a **restrição de analogia** ("não use dicionário") evitou uma resposta previsível.

---

## Validação

- **Fontes consultadas:**
  - Material didático da disciplina (aula sobre algoritmos de busca).
  - Khan Academy — "Binary search".
  - Cormen et al., *Introduction to Algorithms*, cap. 2.

- **Pontos corrigidos:**
  - A IA afirmou no P1 que busca binária é "muito mais eficiente" que a linear — corrigi para "mais eficiente em vetores grandes e ordenados".
  - O pré-requisito de ordenação não estava destacado no P1 — complementado com fonte externa.

- **Pontos incertos:**
  - "Ordenar pode custar mais caro que uma busca linear" — verdadeiro em geral (O(n log n) vs. O(n)), mas depende do número de buscas; registrei a ressalva.

- **Explicação com minhas palavras:** o passo a passo foi reproduzido manualmente para confirmar cada iteração.

---

## Reflexão

### 1. Qual foi a principal diferença entre os prompts?

A explicitação da **intenção** — objetivo e critério de qualidade —, não o tamanho. O P1 pedia "uma explicação"; o P3 pedia "uma explicação que permita ao aluno executar X e reconhecer Y".

### 2. Quais elementos tiveram maior impacto?

Critério de qualidade e contexto. O critério forçou a IA a calibrar profundidade, incluir verificação e detalhar o cálculo do meio.

### 3. Um prompt maior é necessariamente melhor?

Não. O P2 (menor que o P3) já resolveu a maior parte do problema. O P3 só melhorou porque adicionou **informação relevante**, não palavras.

### 4. O que ocorre quando o objetivo não é claro?

A IA assume o objetivo mais provável — geralmente o mais genérico — e produz uma resposta tecnicamente correta, mas pouco útil para o contexto real.

### 5. Quais informações são indispensáveis?

Objetivo, público e contexto. Sem esses três, a IA não calibra profundidade, linguagem nem escolha de exemplos.

### 6. Como essa habilidade pode ser utilizada profissionalmente?

- **Revisão de código:** análise com critérios explícitos.
- **Documentação técnica:** público e formato definidos antes do texto.
- **Ideação de arquitetura:** contexto e restrições fornecidos.
- **Testes:** critérios de aceitação antes de pedir casos de teste.
- **Roteiros de estudo:** objetivo de aprendizagem e nível prévio explícitos.

### 7. Quais riscos existem ao confiar automaticamente na IA?

Conceitos incorretos com confiança, referências inventadas, generalizações, dados desatualizados e — o mais perigoso — a sensação de que "está bem escrito, logo está certo".

### 8. Houve situação em que o Prompt 3 ficou pior que o Prompt 2?

Sim: a restrição "não use dicionário" fez a IA usar uma analogia ligeiramente mais abstrata. Nesse aspecto isolado, o P2 foi mais natural. Mas o ganho no passo a passo, na tabela e na verificação compensou.

### 9. Existe um ponto em que adicionar mais instruções prejudica?

Sim. Quando as instruções competem entre si ("seja detalhado" + "máx. 200 palavras") ou quando o excesso de restrições engessa a resposta — a IA passa a "cumprir checklist" em vez de explicar bem.

### 10. O que você faria para verificar se a resposta tecnicamente está correta?

Fonte externa independente, execução manual ou em código, comparação com o material da disciplina e reescrita com as próprias palavras.

---

## Take Away

> **Um bom prompt não é simplesmente um prompt longo. Ele precisa...**
>
> ...explicitar **intenção** (objetivo + público + contexto), **delimitar** (formato + restrições) e **permitir verificação** (critério de qualidade). Tamanho é consequência, não meta.

---

## Cinco recomendações

1. **Comece pelo objetivo, não pelo verbo.** "Explique X" é vago; "faça o aluno conseguir executar X manualmente" é acionável.
2. **Declare o público e o que ele já sabe** — calibra profundidade melhor que "seja didático".
3. **Defina um critério de qualidade verificável** ("ao final, o aluno deve conseguir..."). É o elemento que mais muda a resposta.
4. **Use restrições para excluir o óbvio** ("não use dicionário", "sem fórmulas") — evita respostas previsíveis.
5. **Valide sempre em fonte externa.** Prompt bom não dispensa checagem; ele só torna a checagem mais fácil.
