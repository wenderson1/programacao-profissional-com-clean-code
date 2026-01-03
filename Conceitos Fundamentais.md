## Princípios SOLID

# Fundamentos do Clean Code: Introdução ao SOLID

Este documento resume os conceitos fundamentais abordados no módulo introdutório do curso de Programação Profissional com Clean Code. Antes de aplicar as práticas do livro Clean Code, é essencial dominar estes princípios.

## Visão Geral
O Clean Code não inventou novos princípios; ele é uma coleção de práticas consagradas. Para aplicar o Clean Code corretamente, é necessário ter uma base sólida, e essa base é o **SOLID**.

O nome "SOLID" sugere a criação de um código robusto (sólido), em oposição a um código frágil.

## O Acrônimo SOLID Explicado

O SOLID é composto por cinco princípios fundamentais da orientação a objetos. Abaixo, o significado de cada um:

### 1. S - SRP (Single Responsibility Principle)
**Princípio da Responsabilidade Única**
*   **Definição:** Uma classe deve ter um, e apenas um, motivo para mudar.
*   **Na prática:** Significa que uma classe deve ser especializada em uma única tarefa ou conceito de negócio. Se uma classe gerencia banco de dados, envia e-mails e calcula impostos, ela está violando o SRP.

### 2. O - OCP (Open/Closed Principle)
**Princípio do Aberto/Fechado**
*   **Definição:** Entidades de software (classes, módulos, funções, etc.) devem estar abertas para extensão, mas fechadas para modificação.
*   **Na prática:** Você deve ser capaz de mudar o comportamento de uma classe sem alterar o código fonte dela (geralmente usando herança ou interfaces). Isso evita que alterações quebrem funcionalidades já existentes.

### 3. L - LSP (Liskov Substitution Principle)
**Princípio da Substituição de Liskov**
*   **Definição:** Subclasses devem ser substituíveis por suas superclasses sem quebrar a aplicação.
*   **Na prática:** Se você tem uma classe `Pássaro` e uma subclasse `Pinguim`, e `Pássaro` tem um método `voar()`, o `Pinguim` não deveria herdar de `Pássaro` se ele não voa (ou teria que lançar um erro, o que viola o princípio). A herança deve fazer sentido comportamental, não apenas estrutural.

### 4. I - ISP (Interface Segregation Principle)
**Princípio da Segregação de Interface**
*   **Definição:** Muitas interfaces específicas são melhores do que uma interface única geral.
*   **Na prática:** Uma classe não deve ser forçada a implementar métodos que ela não usa. É melhor criar várias interfaces pequenas (ex: `Imprimível`, `Digitalizável`) do que uma interface gigante (`MáquinaFazTudo`) que obriga uma impressora simples a implementar um método de digitalização vazio.

### 5. D - DIP (Dependency Inversion Principle)
**Princípio da Inversão de Dependência**
*   **Definição:** Módulos de alto nível não devem depender de módulos de baixo nível. Ambos devem depender de abstrações. Abstrações não devem depender de detalhes. Detalhes devem depender de abstrações.
*   **Na prática:** Em vez de uma classe `Venda` instanciar diretamente uma classe `MySQLConnection` (dependência forte), ela deve depender de uma interface `BancoDeDados`. Assim, você pode trocar o MySQL por PostgreSQL sem tocar no código da `Venda`.

---

## A "Dica de Ouro" do Instrutor

Um dos pontos mais importantes destacados na aula é a hierarquia de importância dentro do SOLID:

> **"Tudo sobre SOLID é basicamente sobre SRP (Responsabilidade Única)."**

*   O **SRP** é a base de tudo.
*   Os outros quatro princípios (OCP, LSP, ISP, DIP) muitas vezes servem como ferramentas ou meios para tornar o SRP possível.
*   Você não consegue resolver problemas de arquitetura apenas "quebrando" o código em pedaços menores; você precisa de técnicas de abstração e inversão de controle (os outros princípios) para garantir que cada classe tenha realmente apenas uma responsabilidade.

## Conclusão
As boas práticas de Clean Code giram em torno do SRP. Se você ainda não domina o SOLID, é recomendável estudar esses conceitos a fundo antes de prosseguir, pois eles guiarão as tomadas de decisão para a escrita de um código limpo.

# Fundamentos do Clean Code: Princípios Essenciais

Além do SOLID, existem outros princípios e conceitos fundamentais que devem guiar a escrita de um código limpo e profissional. Este documento resume as práticas essenciais para garantir manutenibilidade, clareza e eficiência no desenvolvimento de software.

## 1. Princípios de Design (DRY, KISS, YAGNI)

### DRY (Don't Repeat Yourself)
*   **Conceito:** "Não se repita". Cada parte do conhecimento da aplicação deve ter uma representação única e inequívoca.
*   **Objetivo:** Evitar duplicação de código para facilitar a manutenção. Se uma regra de negócio muda, você deve alterá-la em apenas um lugar.
*   **Exemplo de Violação:** Ter dois métodos em classes diferentes que calculam a área de um retângulo com a mesma lógica.
*   **Observação:** O DRY também se aplica à redundância desnecessária, como declarar explicitamente o tipo de uma variável quando o compilador já consegue inferi-lo (ex: `int numero = 0` vs `var numero = 0`).

### KISS (Keep It Simple, Stupid)
*   **Conceito:** "Mantenha isso simples". Enfatiza a simplicidade no design e na implementação.
*   **Objetivo:** Evitar complexidade desnecessária. Códigos simples são mais fáceis de entender, manter e têm menor probabilidade de erros.
*   **Aplicação:** Se um código está muito verboso ou complexo, ele deve ser refatorado. Use recursos da linguagem/framework para simplificar tarefas (ex: usar métodos prontos de manipulação de strings em vez de criar loops manuais).

### YAGNI (You Ain't Gonna Need It)
*   **Conceito:** "Você não vai precisar disso".
*   **Objetivo:** Não implementar funcionalidades baseadas em suposições futuras. Foque apenas no que é necessário agora.
*   **Risco:** Código criado "para o caso de precisar no futuro" gera custo de manutenção, pode conter bugs e muitas vezes nunca chega a ser utilizado ou, quando é, a necessidade já mudou.
*   **Regra de Ouro:** Um bom arquiteto adia decisões até o último momento responsável.

---

## 2. Acoplamento e Coesão

Estes dois conceitos andam juntos e são vitais para atingir o SRP (Princípio da Responsabilidade Única).

### Acoplamento (Coupling)
Refere-se ao grau de dependência entre módulos ou classes.
*   **Acoplamento Forte (Ruim):** Mudanças em um módulo quebram ou exigem mudanças em outro. Ex: Instanciar classes concretas com `new` dentro de outras classes.
*   **Acoplamento Fraco (Bom):** Módulos independentes que se comunicam via abstrações (interfaces). Facilita testes e manutenção.
*   **Dica:** Use Injeção de Dependência para reduzir o acoplamento.

### Coesão (Cohesion)
Refere-se ao grau em que os elementos de um módulo pertencem uns aos outros e focam em um único propósito.
*   **Baixa Coesão (Ruim):** Uma classe "Funcionário" que calcula salário, gera relatório e agenda reuniões. Faz coisas demais e não relacionadas.
*   **Alta Coesão (Bom):** Classes especializadas que trabalham juntas (ex: `CalculadoraDeSalario`, `GeradorDeRelatorio`). Cada uma tem uma responsabilidade clara.

---

## 3. Funções Puras vs. Impuras

### Funções Puras
*   **Determinismo:** Para os mesmos argumentos, retorna sempre o mesmo resultado.
*   **Sem Efeitos Colaterais:** Não altera estados externos, variáveis globais, não acessa banco de dados ou disco.
*   **Vantagens:** Fáceis de testar, compreender e são *thread-safe* (podem rodar em paralelo).

### Funções Impuras
*   Dependem de ou alteram estados externos (ex: salvar no banco de dados, consultar API, ler arquivo).
*   **Estratégia:** Não elimine funções impuras (elas são necessárias), mas **separe-as**. Mantenha a lógica de negócios em funções puras e deixe as impuras apenas para interações com o ambiente externo.

---

## 4. Lei de Demeter (LoD)

Também conhecida como "Princípio do Mínimo Conhecimento".
*   **Regra:** "Não fale com estranhos". Um objeto deve interagir apenas com seus "amigos imediatos" (parâmetros, objetos criados por ele, ou propriedades diretas).
*   **Violação (Tremwreck):** `pedido.cliente.endereco.cidade`. O objeto está acessando propriedades muito profundas.
*   **Solução:** O objeto `pedido` ou `cliente` deveria fornecer um método para acessar a informação necessária (ex: `cliente.getCidade()`), encapsulando a estrutura interna.

---

## 5. As 4 Regras da Simplicidade

Para garantir um código limpo, siga esta ordem de prioridade:
1.  **Rodar todos os testes:** O código deve funcionar e não quebrar nada existente (evitar regressão).
2.  **Revelar intenção:** O código deve ser autoexplicativo. Nomes de variáveis e métodos devem deixar claro o que fazem.
3.  **Não duplicar código:** Eliminar redundâncias (DRY).
4.  **Minimizar entidades:** Ter o menor número possível de classes e métodos, mantendo o sistema enxuto (KISS/YAGNI).

---

## 6. Linguagem Onipresente (Ubiquitous Language)

Um conceito central do DDD (Domain-Driven Design).
*   **Definição:** Uso consistente da mesma terminologia em todo o projeto: conversas, documentação, código e testes.
*   **Objetivo:** Eliminar ambiguidades e falhas de comunicação entre desenvolvedores e especialistas de negócio.
*   **Prática:** Não invente nomes técnicos ("jargões de dev"). Use os termos reais do negócio. Se o negócio chama de "Sinistro", não chame de "Ocorrência" no código.

---

> **Reflexão Final (Martin Fowler):**
> "Qualquer tolo pode escrever um código que um computador entenda. Bons programadores escrevem códigos que os humanos possam entender."
