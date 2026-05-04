# 📐 README — Reflexão sobre Specs e Spec Driven Development

> Este documento descreve o que aprendi sobre **especificações (specs)** durante o desenvolvimento do projeto **Vinho Fino**, como elas foram aplicadas na prática com o OpenSpec, e quais benefícios e desafios identifiquei ao longo do processo.

---

## O que são Specs?

Uma **spec** (especificação) é um documento estruturado que descreve **o que** um sistema ou funcionalidade deve fazer, **por que** deve ser feito dessa forma, e **como** a implementação deve se comportar — tudo isso **antes** de escrever código.

No contexto do **SDD (Spec Driven Development)**, as specs não são apenas documentação: elas são o **ponto de partida do desenvolvimento**. O fluxo se inverte: ao invés de escrever código e depois (talvez) documentar, você especifica primeiro e implementa depois, guiado pela spec.

No OpenSpec, cada mudança no projeto gera automaticamente:
- **`proposal.md`** — descrição da mudança e motivação
- **`design.md`** — decisões de arquitetura e abordagem
- **`tasks.md`** — lista de tarefas derivadas da spec
- **Deltas em `specs/`** — alteração incremental na especificação consolidada do projeto

---

## O papel das Specs no desenvolvimento

Antes de praticar SDD, eu via especificações como "burocracia" — algo que atrasava o começo do trabalho "real" (o código). Depois do projeto, mudei essa visão.

A spec age como uma **conversa antecipada com o problema**. Ela força você a responder perguntas difíceis antes de se comprometer com uma implementação:

- Essa funcionalidade faz sentido aqui?
- Qual é o comportamento esperado nos casos de borda?
- Como isso se integra ao que já existe?
- Quem usa isso e por quê?

No nosso projeto, o comando `/opsx:explore` foi especialmente útil nesse sentido: antes de propor o catálogo de produtos, usamos o explore para discutir dúvidas como "o carrinho deve persistir entre sessões?" e "quais informações são essenciais no card do vinho?". Esse alinhamento prévio evitou retrabalho.

---

## Como as Specs foram aplicadas no projeto

### 1. Catálogo de produtos — `/opsx:propose add-product-catalog`

A spec gerada descreveu que o catálogo deveria exibir vinhos em grid responsivo, com nome, região, ano, preço e avaliação. O `design.md` registrou a decisão de usar dados estáticos em JavaScript (array de objetos) em vez de uma API, pois o escopo era um MVP de front-end. Isso ficou registrado e rastreável, não foi uma decisão "na cabeça do desenvolvedor".

### 2. Carrinho lateral — `/opsx:propose add-cart-sidebar`

Antes da spec, havia dúvida se o carrinho seria uma página separada ou um sidebar. O `proposal.md` listou os prós e contras de cada abordagem. A spec definiu que seria um sidebar deslizante com overlay, e o `tasks.md` quebrou isso em tarefas: criar o HTML do sidebar, implementar a lógica de adicionar/remover itens, calcular o total, e criar o sistema de toast para feedback.

Seguir as tarefas da spec tornou o trabalho mais fluido porque eu sabia exatamente o que precisava ser feito, sem ficar "perdido no código".

### 3. Newsletter — `/opsx:propose add-newsletter`

Aqui a spec foi mais simples, mas ainda útil: definiu que a validação do e-mail deveria ser feita no front-end com feedback visual (toast), sem integração com backend real. Sem a spec, provavelmente alguém teria começado a configurar um servidor ou API desnecessariamente.

---

## Benefícios que as Specs trouxeram

### ✅ Clareza antes de codar
O maior benefício foi a **redução de ambiguidade**. Quando a spec diz "o card deve exibir nome, região, ano, preço e avaliação em estrelas", não há margem para cada membro do grupo implementar uma versão diferente.

### ✅ Rastreabilidade das decisões
Com o `design.md` de cada mudança, conseguimos entender **por que** algo foi feito de um jeito, não só **como**. Quando voltamos para revisar o código semanas depois, não precisamos adivinhar a intenção original.

### ✅ Divisão de trabalho mais fácil
O `tasks.md` gerado pelo `/opsx:propose` funcionou como um mini-backlog natural para cada funcionalidade. Dividir tarefas entre os membros do grupo ficou mais organizado porque as tarefas já estavam definidas pela spec.

### ✅ Menos retrabalho
Antes de praticar SDD, era comum implementar algo, mostrar para o grupo e ouvir "não era bem isso que eu tinha imaginado". Com a spec, o alinhamento acontecia antes do código. O retrabalho caiu visivelmente.

### ✅ Documentação que nasce junto com o projeto
Ao final, o diretório `openspec/specs/` continha uma visão consolidada de todo o projeto. Não foi necessário "documentar depois" — a documentação nasceu naturalmente do processo.

---

## Desafios e Limitações percebidos

### ⚠️ Curva de aprendizado inicial
Os primeiros usos do OpenSpec foram confusos. Entender a diferença entre `/opsx:explore`, `/opsx:propose` e `/opsx:apply`, e quando usar cada um, levou algum tempo. A tentação de "só codar logo" era grande, especialmente no início do projeto.

### ⚠️ Specs podem engessar se mal utilizadas
Em um momento do projeto, a spec do carrinho definia que ele deveria ter uma funcionalidade de "quantidade por item" (incrementar/decrementar). No meio da implementação, percebemos que para um MVP simples, bastava adicionar e remover. Atualizar a spec para refletir essa mudança gerou um passo extra que às vezes parecia burocrático.

A lição foi que **specs não são imutáveis** — elas devem ser atualizadas quando as decisões mudam. Mas isso exige disciplina.

### ⚠️ Overhead para mudanças pequenas
Para ajustes cosméticos simples (mudar uma cor, ajustar um espaçamento), criar uma spec formal parecia desproporcional. O OpenSpec funciona melhor para mudanças com impacto funcional real. Para tweaks visuais menores, é razoável não seguir o fluxo completo.

### ⚠️ A qualidade da spec depende da qualidade das perguntas
O `/opsx:explore` só é útil se você realmente levantar as dúvidas certas antes de propor. Se você entrar no explore com os requisitos já "decididos na cabeça", o processo vira protocolo vazio. A ferramenta auxilia, mas não substitui o pensamento crítico sobre o problema.

---

## Conclusão

Praticar SDD com OpenSpec mudou a forma como encaro o começo de uma funcionalidade. Antes eu abria o editor de código imediatamente; agora, meu primeiro instinto é perguntar: "Eu sei o suficiente para escrever uma spec disso?"

As specs não são o oposto da agilidade — elas são uma forma de ser ágil de maneira mais inteligente, evitando retrabalho e decisões implícitas que assombram o projeto mais tarde.

O maior aprendizado foi entender que **especificar não é prever o futuro perfeito**. É criar um registro compartilhado do que o time sabe e decidiu até agora, com consciência de que isso pode evoluir.

---

*Projeto desenvolvido na disciplina de Engenharia de Software — aplicação de Spec Driven Development com OpenSpec.*
