# Fundamentos de Clean Code: Funções (Métodos)

Este documento resume as melhores práticas de programação profissional abordadas no módulo de "Funções". As funções (ou métodos/comportamentos) são componentes fundamentais do desenvolvimento de software. Escrevê-las corretamente melhora a legibilidade, a manutenibilidade e a reutilização do código.

---

## 1. Definição e Importância

Funções são blocos de código projetados para realizar uma tarefa específica. No contexto de Orientação a Objetos, são frequentemente chamadas de **métodos** ou **comportamentos**.

**Por que se preocupar com a qualidade das funções?**
*   Facilitam a leitura do código.
*   Tornam a manutenção mais simples e menos propensa a erros.
*   Permitem o reaproveitamento de lógica em diferentes partes do sistema.

---

## 2. A Regra de Ouro: Simplicidade e Tamanho

A principal regra para escrever funções limpas é: **Elas devem ser pequenas.**

### 2.1. Quão pequenas?
*   Funções não devem ter centenas de linhas.
*   Historicamente, dizia-se que uma função deveria caber em uma tela (para não precisar rolar). Hoje, com monitores grandes, a regra é mais sobre **responsabilidade** do que pixels.
*   Se uma função é muito grande, provavelmente ela está fazendo coisas demais.

### 2.2. Faça apenas uma coisa (Single Responsibility Principle)
Uma função deve fazer **uma coisa**, deve fazê-la **bem** e deve fazer **apenas ela**.

*   **Sintoma de quebra de regra:** Se você consegue extrair um trecho da sua função e dar a ele um nome que não seja apenas uma reformulação da implementação, então sua função original estava fazendo mais de uma coisa.
*   **Exemplo:** Uma função `CadastrarUsuario` não deve validar o CPF, abrir conexão com banco, salvar o usuário e enviar e-mail de boas-vindas. Ela deve orquestrar chamadas para outras funções que fazem essas tarefas individualmente.

---

## 3. Níveis de Abstração

Para garantir que uma função faça apenas uma coisa, certifique-se de que todas as instruções dentro dela estejam no **mesmo nível de abstração**.

*   **Alto Nível:** Regras de negócio gerais (ex: `ObterRelatorio()`).
*   **Baixo Nível:** Detalhes de implementação técnica (ex: `string.Append()`, `html.Render()`).

**A Regra Descendente (The Step-down Rule):**
O código deve ser lido de cima para baixo como uma narrativa jornalística. As funções de alto nível vêm primeiro, seguidas pelas funções de nível inferior que elas chamam.

---

## 4. Blocos e Indentação

*   **Blocos `if`, `else`, `while`, etc.:** Devem ter, idealmente, apenas uma linha de código (geralmente uma chamada de função).
*   **Nível de Indentação:** Uma função não deve ter muitos níveis de indentação aninhados. Isso aumenta a complexidade cognitiva. Tente manter no máximo um ou dois níveis.

---

## 5. Parâmetros de Função

A quantidade ideal de argumentos para uma função é **zero (niládica)**. Depois **um (monádica)**, depois **dois (diádica)**. Três argumentos (triádica) devem ser evitados sempre que possível. Mais de três (poliádica) exige uma justificativa muito forte (e geralmente indica um problema de design).

### Por que evitar muitos parâmetros?
1.  **Dificuldade de Leitura:** O leitor precisa entender o significado de cada argumento.
2.  **Dificuldade de Teste:** Testar todas as combinações possíveis de 4 ou 5 argumentos é exponencialmente difícil.

### Como resolver?
Se uma função precisa de muitos argumentos (ex: criar um usuário com nome, idade, endereço, telefone), é provável que esses argumentos devam ser agrupados em uma classe ou estrutura própria (ex: um objeto `DadosUsuario` ou DTO).

---

## 6. Evite Efeitos Colaterais (Side Effects)

Uma função promete fazer uma coisa (pelo seu nome), mas escondido ela faz outra. Isso é um efeito colateral e é perigoso.

*   **Exemplo Perigoso:** Uma função chamada `VerificarSenha(usuario, senha)` que, além de verificar a senha, inicializa a sessão do usuário se a senha estiver correta.
*   **Problema:** Quem chama `VerificarSenha` pode querer apenas validar a credencial sem logar o usuário, mas acabará alterando o estado do sistema sem saber.
*   **Solução:** Renomeie a função para `VerificarSenhaEInicializarSessao` (o que viola a regra de fazer uma só coisa) ou separe as responsabilidades.

---

## 7. Resumo das Boas Práticas

1.  **Nomes Descritivos:** O nome deve explicar o que a função faz. Nomes longos e descritivos são melhores que nomes curtos e enigmáticos.
2.  **Pequenas:** Mantenha as funções curtas.
3.  **Uma Coisa Só:** Foque em uma única responsabilidade.
4.  **Menos Argumentos:** Reduza a quantidade de parâmetros ao mínimo necessário.
5.  **Sem Efeitos Colaterais:** Não altere estados do sistema de forma oculta.

> *"Funções são os verbos da linguagem de programação, e as classes são os substantivos. Escrever funções limpas é a arte de contar a história do sistema de forma clara e fluida."*
