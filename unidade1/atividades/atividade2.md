# Engenharia de Prompt - Atividade

## 1. Identificação:

- **Disciplina:** Tendências em Ciência da Computação
- **Professora:** Kadidja Valéria Reginaldo de Oliveira
- **Integrante:** João Ricardo Barbosa Matos
- **Matrícula:** 33306109


## 2. Problema escolhido

**Contexto:** Uma equipe de desenvolvimento está criando um sistema acadêmico simples (cadastro de alunos, matrícula em disciplinas e lançamento de notas). A equipe precisa planejar a etapa de testes, mas os membros têm pouca experiência em escrever casos de teste formais.

**Problema:** A equipe não sabe como estruturar casos de teste que cubram os cenários principais e os casos de exceção do sistema, nem quais informações cada caso de teste deve conter.

**Objetivo:** Utilizar IA generativa para produzir um conjunto de casos de teste para o módulo de matrícula, servindo como ponto de partida para a equipe revisar, validar e complementar.


## 3. Objetivo

Obter, com apoio de IA, casos de teste claros e organizados para o módulo de matrícula do sistema acadêmico, que cubram cenários positivos, negativos e de exceção, e que possam ser revisados criticamente pela equipe antes de sua adoção.


## 4. Prompt inicial

```text
Crie casos de teste para um sistema acadêmico.
```

### Resultado inicial

> **Casos de Teste — Sistema Acadêmico**
>
> 1. **CT01 — Cadastro de aluno:** verificar se o aluno é cadastrado com dados válidos.
> 2. **CT02 — Matrícula em disciplina:** verificar se o aluno consegue se matricular em uma disciplina.
> 3. **CT03 — Lançamento de notas:** verificar se a nota é registrada corretamente.
> 4. **CT04 — Exclusão de aluno:** verificar se o aluno é removido do sistema.
> 5. **CT05 — Consulta de notas:** verificar se o aluno visualiza suas notas.

> ⚠️ **Nota:** resultado simulado para fins didáticos. Substitua pelo resultado obtido em uma ferramenta real de IA generativa.

---

## 5. Análise crítica

| Questão | Resposta |
|---|---|
| A resposta atendeu ao objetivo? | **Parcialmente.** Trouxe casos genéricos, mas sem detalhamento suficiente para execução. |
| A resposta foi clara? | **Pouco.** Os casos são vagos ("verificar se..."), sem passos, dados de entrada ou resultado esperado. |
| O que ficou faltando? | Pré-condições, passos de execução, dados de entrada, resultado esperado, casos negativos e de exceção, prioridade. |
| O que poderia ser melhorado? | Estrutura em tabela, foco no módulo de matrícula, cobertura de cenários de erro (turma lotada, aluno inexistente, matrícula duplicada). |
| Existem informações que precisam ser verificadas? | Sim — as regras de negócio da matrícula (limite de disciplinas, pré-requisitos) **não foram consideradas**. |
| A IA fez alguma suposição inadequada? | Sim: assumiu um sistema genérico e ignorou regras de negócio específicas do contexto. |

**Conclusão da análise:** o prompt inicial é ambíguo (não define escopo, formato nem critérios), gerando uma resposta superficial e genérica — exatamente o que a aula alerta sobre prompts pouco estruturados.

---

## 6. Prompt refinado

```text
PAPEL:
Você é um analista de testes de software (QA) experiente.

CONTEXTO:
Estamos desenvolvendo um sistema acadêmico simples com os módulos de cadastro de alunos,
matrícula em disciplinas e lançamento de notas. A equipe tem pouca experiência em testes.
O foco desta tarefa é o MÓDULO DE MATRÍCULA.

OBJETIVO:
Criar um conjunto de casos de teste que sirva de ponto de partida para a equipe revisar e validar.

TAREFA:
Elabore casos de teste para o módulo de matrícula, cobrindo:
- cenários positivos (matrícula bem-sucedida);
- cenários negativos (dados inválidos, aluno inexistente);
- cenários de exceção (turma lotada, matrícula duplicada, disciplina sem vagas, aluno sem pré-requisito).

RESTRIÇÕES:
- Considere as seguintes regras de negócio:
  (1) um aluno pode matricular-se em no máximo 5 disciplinas por semestre;
  (2) não é permitido matricular-se duas vezes na mesma disciplina;
  (3) a disciplina deve ter vagas disponíveis;
  (4) o aluno deve ter cursado o pré-requisito, quando houver.
- Gere no máximo 10 casos de teste.
- Utilize linguagem clara, adequada para iniciantes em testes.

FORMATO:
Apresente os casos em uma tabela com as colunas:
ID | Descrição | Pré-condição | Dados de entrada | Passos | Resultado esperado | Tipo (positivo/negativo/exceção) | Prioridade

CRITÉRIOS DE QUALIDADE:
Os casos devem ser claros, objetivos, rastreáveis às regras de negócio, cobrir cenários positivos e de exceção
e ser executáveis por alguém com conhecimento básico de testes.
```

---

## 7. Resultado refinado

| ID | Descrição | Pré-condição | Dados de entrada | Passos | Resultado esperado | Tipo | Prioridade |
|---|---|---|---|---|---|---|---|
| CT01 | Matrícula válida em disciplina com vaga | Aluno cadastrado; disciplina com vagas | ID aluno 123; código DISC01 | 1. Acessar matrícula. 2. Informar aluno e disciplina. 3. Confirmar. | Matrícula registrada com sucesso | Positivo | Alta |
| CT02 | Matrícula em disciplina lotada | Disciplina sem vagas | ID aluno 123; DISC02 (0 vagas) | 1. Tentar matricular. | Sistema bloqueia e exibe "sem vagas" | Exceção | Alta |
| CT03 | Matrícula duplicada | Aluno já matriculado em DISC01 | ID aluno 123; DISC01 | 1. Tentar matricular novamente. | Sistema bloqueia e informa duplicidade | Exceção | Alta |
| CT04 | Aluno inexistente | — | ID aluno 999 (não cadastrado) | 1. Tentar matricular. | Sistema exibe erro "aluno não encontrado" | Negativo | Média |
| CT05 | Limite de 5 disciplinas excedido | Aluno já matriculado em 5 disciplinas | ID aluno 123; DISC06 | 1. Tentar 6ª matrícula. | Sistema bloqueia e informa limite excedido | Exceção | Alta |
| CT06 | Pré-requisito não cumprido | Aluno sem o pré-requisito de DISC03 | ID aluno 123; DISC03 | 1. Tentar matricular. | Sistema bloqueia e informa pré-requisito pendente | Exceção | Alta |
| CT07 | Matrícula com dados incompletos | — | Disciplina em branco | 1. Confirmar sem selecionar disciplina. | Sistema exibe validação de campo obrigatório | Negativo | Média |
| CT08 | Matrícula válida em segunda disciplina | Aluno com 1 matrícula | ID aluno 123; DISC04 | 1. Matricular em DISC04. | Matrícula registrada | Positivo | Média |

> ⚠️ **Nota:** resultado simulado para fins didáticos. Substitua pelo resultado obtido em uma ferramenta real de IA generativa.

---

## 8. Comparação

| Critério | Prompt A (inicial) | Prompt B (refinado) |
|---|---|---|
| **Clareza** | Baixa — casos vagos | Alta — estrutura definida e passos explícitos |
| **Contexto** | Ausente | Presente — sistema, módulo e equipe descritos |
| **Relevância** | Genérica (todo o sistema) | Focada no módulo de matrícula |
| **Organização** | Lista simples | Tabela com 8 colunas |
| **Precisão** | Sem resultado esperado | Resultado esperado por caso |
| **Utilidade** | Baixa — não executável | Alta — executável e rastreável às regras |

**Qual prompt produziu o resultado mais adequado? Por quê?**

O **Prompt B**. Porque define papel, contexto, objetivo, tarefa, restrições (incluindo regras de negócio), formato e critérios de qualidade — exatamente os elementos da anatomia do prompt estudados na aula. O resultado é mais específico, organizado, executável e cobre cenários positivos, negativos e de exceção. O Prompt A gerou uma resposta superficial porque deixou a IA fazer suposições.

---

## 9. Técnica aplicada

- [x] Refinamento iterativo
- [ ] Outra: ___________

---

## 10. Teste de robustez (etapa complementar)

**Variável alterada:** o nível de detalhamento do público.

- **Versão A:** "Utilize linguagem clara, adequada para iniciantes em testes."
- **Versão B:** "Utilize linguagem técnica formal, com terminologia padrão de QA (ex.: *fixture*, *assert*, *boundary value*), destinada a analistas de teste certificados."

**Registro:**

- **O que mudou na resposta?** A Versão B tende a produzir casos mais técnicos, com nomenclatura formal e maior rigor, porém menos acessíveis à equipe iniciante.
- **Por que acreditamos que mudou?** Porque o público-alvo declarado orienta o vocabulário e o nível de detalhe da IA.
- **A alteração melhorou ou piorou?** Para o contexto real (equipe iniciante), a **Versão A é mais adequada**; a Versão B seria melhor para uma equipe experiente. Isso mostra que o público é uma variável crítica do prompt.

---

## 11. Validação

O resultado foi verificado por meio de:

1. **Rastreabilidade às regras de negócio:** cada caso foi conferido contra as 4 regras informadas no prompt (limite de 5 disciplinas, duplicidade, vagas, pré-requisito).
2. **Revisão da equipe:** os casos foram discutidos em grupo para checar coerência e viabilidade.
3. **Consulta a fontes de teste:** comparação com boas práticas de teste (partição de equivalência e análise de valor limite) para verificar cobertura.
4. **Execução simulada:** verificação mental dos passos para garantir que cada caso é executável.

> ⚠️ A IA pode inventar regras ou omitir cenários; por isso a validação humana é indispensável.

---

## 12. Ética e responsabilidade

Riscos no uso da IA neste problema:

- **Casos de teste incompletos ou incorretos**, dando falsa sensação de cobertura.
- **Suposições silenciosas** sobre regras de negócio não informadas.
- **Viés de cobertura** (focar só em cenários felizes).
- **Excesso de confiança** na resposta por ela parecer bem escrita.
- **Confidencialidade:** não inserir dados reais sensíveis de alunos nos prompts.

**Responsabilidade:** a equipe é responsável por revisar, validar e complementar os casos antes de usá-los; a IA é ferramenta de apoio, não substituta do julgamento humano.

---

## 13. Take Away

O integrante aprendeu que a **qualidade da resposta depende diretamente da estrutura do prompt**: quanto mais claros papel, contexto, objetivo, tarefa, restrições e formato, mais útil e executável é o resultado. Também compreendeu que a Engenharia de Prompt é **iterativa** — o prompt inicial raramente é suficiente — e que a **validação crítica** é parte essencial do processo, pois a IA pode ser convincente e ainda assim estar errada ou incompleta.

---

## 14. Link

- [Repositório da disciplina]([https://github.com/[usuario]/[repositorio]](https://github.com/matosjoaoricardo-gif/tendencias_em_ciencia_da_computacao_JR))
- [Arquivo no GitHub]([https://github.com/[usuario]/[repositorio]/blob/main/aula-02/engenharia-de-prompt.md](https://github.com/matosjoaoricardo-gif/tendencias_em_ciencia_da_computacao_JR/edit/main/unidade1/atividades/atividade2.md))
