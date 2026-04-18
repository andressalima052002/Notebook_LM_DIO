# 📘 Estudo sobre SQL Server

## 🎯 Contexto e Objetivo

Este repositório tem como objetivo estruturar conhecimentos sobre o **SQL Server**, abordando seus principais conceitos, funcionalidades e utilidades no contexto de banco de dados.

O foco do estudo é compreender como o SQL Server funciona na prática, incluindo manipulação de dados, consultas, segurança e arquitetura básica.

O SQL Server é um sistema gerenciador de banco de dados relacional (RDBMS) utilizado para armazenar, processar e gerenciar dados, sendo amplamente utilizado em ambientes corporativos ([TechTarget][1]).

---

## 📚 Curadoria de Fontes

### 🎥 Vídeos

* https://www.youtube.com/watch?v=Gh19B72SepY
* https://www.youtube.com/watch?v=y8tzjzSEO5s
* https://www.youtube.com/watch?v=9lIeeVTTC5s

---

### 📄 Documentação Oficial

* https://learn.microsoft.com/pt-br/sql/sql-server/what-is-sql-server?view=sql-server-ver17
* https://learn.microsoft.com/pt-br/sql/database-engine/sql-database-engine?view=sql-server-ver17&tabs=dba
* https://learn.microsoft.com/pt-br/sql/sql-server/connect-to-database-engine?view=sql-server-ver17&tabs=sqldb

📌 O Database Engine é o componente principal do SQL Server, responsável por armazenar, processar e proteger os dados ([Microsoft Learn][2]).
📌 A conexão ao SQL Server é feita por ferramentas como SSMS ou via linha de comando, utilizando instância, protocolo e porta ([Microsoft Learn][3]).

---

## 🧠 Engenharia de Prompts

Durante o estudo, foram utilizados prompts para aprofundar o entendimento:

### Exemplos de Prompts

* “Qual a diferença entre DELETE, TRUNCATE e DROP?”
* “O que são subqueries e quando usar?”
* “Qual a diferença entre roles fixas e roles customizadas?”

### 💡 Estratégia utilizada

* Fazer perguntas diretas e objetivas
* Pedir explicações com exemplos práticos
* Focar em cenários reais de uso

### ⚠️ Dificuldades encontradas

* Algumas fontes não traziam explicações completas
* Necessidade de complementar com conhecimento externo
* Diferença entre teoria e prática

## 🤖 Registro de Respostas do NotebookLM

Durante o estudo, utilizei o NotebookLM para obter explicações e aprofundar o entendimento sobre conceitos do SQL Server.  
Abaixo estão as respostas obtidas a partir dos prompts aplicados.

---

### 🗑️ Prompt: Qual a diferença entre DELETE, TRUNCATE e DROP?

**Resposta:**

Embora as fontes fornecidas discutam extensivamente os componentes do SQL Server, como o Database Engine, e categorizem a linguagem Transact-SQL (T-SQL) em elementos de DDL (Linguagem de Definição de Dados) e DML (Linguagem de Manipulação de Dados), elas não detalham especificamente as definições e diferenças entre os comandos DELETE, TRUNCATE e DROP.

Com base em conhecimentos externos ao material fornecido, aqui está a explicação de como esses comandos funcionam e se diferenciam:

1. DELETE (Comando DML)  
O comando DELETE é utilizado para remover linhas de uma tabela.  

Como funciona: Ele permite o uso da cláusula WHERE para especificar quais registros devem ser excluídos. Se não houver filtro, todas as linhas serão removidas, mas a estrutura da tabela permanece intacta.  

Log e Performance: É uma operação que consome mais recursos, pois o SQL Server registra a exclusão de cada linha individualmente no log de transações, garantindo as propriedades ACID (especificamente a atomicidade e durabilidade para permitir um rollback).  

Gatilhos: Ativa gatilhos (triggers) de exclusão.

---

2. TRUNCATE (Comando DDL)  
O TRUNCATE TABLE remove todas as linhas de uma tabela, mas de uma forma mais "bruta" e rápida que o DELETE.  

Como funciona: Ele não permite o uso de filtros (WHERE). Ele limpa a tabela completamente e reinicia qualquer contador de identidade (como o IDENTITY de uma coluna ID).  

Log e Performance: É categorizado como um comando DDL. Em vez de registrar cada linha removida, ele registra a desalocação das páginas de dados que a tabela ocupava. Por isso, é muito mais rápido e gera um log de transações mínimo.  

Gatilhos: Não ativa gatilhos de exclusão.

---

3. DROP (Comando DDL)  
O comando DROP TABLE é o mais radical de todos, pois elimina o objeto por completo.  

Como funciona: Ele remove não apenas os dados, mas também a estrutura da tabela, seus índices, permissões, gatilhos e restrições. Após um DROP, a tabela deixa de existir no banco de dados.  

Uso: É utilizado quando uma tabela não é mais necessária no esquema do banco de dados.

---

### 🔎 Prompt: O que são subqueries e quando usar?

**Resposta:**

Com base nos documentos fornecidos, as subqueries (subconsultas) são listadas como um dos recursos fundamentais para o desenvolvimento de consultas no SQL Server, dentro da categoria "Query" (Consulta). No entanto, as fontes fornecidas não apresentam uma definição técnica detalhada ou exemplos de aplicação prática para esse comando específico.

Para complementar sua compreensão, apresento abaixo uma explicação baseada em conhecimentos de mercado sobre o tema, uma vez que o detalhamento não consta nas fontes:

O que são Subqueries? (Informação externa)  
Uma subquery é, essencialmente, uma consulta SQL aninhada dentro de outra instrução SELECT, INSERT, UPDATE ou DELETE, ou dentro de outra subquery. Ela funciona como uma consulta interna que fornece dados para a consulta principal (externa).

Quando usar? (Informação externa)  

- Filtragem de dados dinâmica  
- Verificação de existência (IN, ANY, ALL, EXISTS)  
- Cálculos em colunas (subqueries escalares)  
- Substituição de JOIN em alguns cenários  

---

### 🔐 Prompt: Qual a diferença entre roles fixas e roles customizadas?

**Resposta:**

Com base nos documentos fornecidos, as fontes mencionam a segurança como uma das funções principais do Database Engine (Mecanismo de Banco de Dados) e listam o gerenciamento de segurança e permissões como responsabilidades do Administrador de Banco de Dados (DBA). No entanto, os documentos não detalham especificamente a diferença técnica entre roles (funções) fixas e customizadas.

Como essa distinção específica não consta nas fontes, apresento abaixo uma explicação baseada em conhecimentos gerais sobre SQL Server para auxiliá-lo:

Roles Fixas (Informação fora das fontes)  

As roles fixas são papéis de segurança pré-configurados que já vêm com o SQL Server. Elas possuem um conjunto de permissões que não podem ser alteradas.

- Server-level Roles (ex: sysadmin, bulkadmin)  
- Database-level Roles (ex: db_owner, db_datareader)  

Vantagem: Facilidade de uso e padronização.

---

Roles Customizadas (Informação fora das fontes)  

As roles customizadas (ou definidas pelo usuário) são criadas pelo administrador para atender a necessidades específicas de segurança.

Como funcionam: O DBA cria a role e atribui manualmente apenas as permissões necessárias.

Vantagem: Permite seguir o princípio do menor privilégio, aumentando a segurança do ambiente.

---

## 🧠 Considerações sobre o uso do NotebookLM

- Auxiliou na organização das respostas  
- Nem sempre trouxe respostas completas  
- Foi necessário complementar com conhecimento externo  
- Útil para consolidar conceitos e gerar explicações estruturadas
---

## 📘 Mini Guia de Estudo

### 🧾 Resumos Estruturados

#### 🗑️ DELETE, TRUNCATE e DROP

- **DELETE**
  - Remove dados com possibilidade de filtro (`WHERE`)
  - Mantém estrutura da tabela
  - Registra linha a linha no log
  - Permite rollback
  - Dispara triggers

- **TRUNCATE**
  - Remove todos os dados sem filtro
  - Mais rápido que DELETE
  - Reseta IDENTITY
  - Log mínimo
  - Não dispara triggers

- **DROP**
  - Remove a tabela completamente
  - Apaga estrutura, dados e objetos relacionados
  - Não pode ser revertido facilmente

---

#### 🔎 Subqueries

- Consulta dentro de outra consulta
- Pode ser usada em `SELECT`, `INSERT`, `UPDATE` e `DELETE`
- Tipos principais:
  - Escalar (retorna 1 valor)
  - Múltiplas linhas (`IN`, `EXISTS`)
- Usos comuns:
  - Filtros dinâmicos
  - Cálculos
  - Verificação de existência

---

#### 🔐 Roles no SQL Server

- **Roles Fixas**
  - Já existem no SQL Server
  - Permissões pré-definidas
  - Ex: `db_owner`, `db_datareader`

- **Roles Customizadas**
  - Criadas pelo DBA
  - Permissões configuráveis
  - Mais seguras (princípio do menor privilégio)

---

### 📖 Glossário

- **DDL (Data Definition Language):** Linguagem usada para definir estruturas (`CREATE`, `DROP`, `ALTER`)
- **DML (Data Manipulation Language):** Linguagem usada para manipular dados (`SELECT`, `INSERT`, `UPDATE`, `DELETE`)
- **Transaction Log:** Registro de todas as operações realizadas no banco
- **Trigger:** Ação automática executada após eventos (`INSERT`, `UPDATE`, `DELETE`)
- **Subquery:** Consulta dentro de outra consulta
- **Role:** Conjunto de permissões atribuídas a usuários
- **IDENTITY:** Coluna com incremento automático
- **Rollback:** Desfaz uma operação
- **Commit:** Confirma uma operação

---

### 🧠 Prompts Reutilizáveis

- “Explique [conceito] de forma simples e com exemplo prático no SQL Server”
- “Qual a diferença entre [conceito A] e [conceito B]?”
- “Em quais cenários reais eu usaria [conceito]?”
- “Quais erros comuns existem ao usar [conceito]?”
- “Como isso funciona no dia a dia de um DBA?”
- “Me dê um exemplo prático usando SQL”

---

## 🚀 Conclusão

O mini guia consolida os principais conceitos estudados sobre SQL Server, facilitando revisões futuras e servindo como material de apoio prático para o dia a dia.

[1]: https://www.techtarget.com/searchdatamanagement/definition/SQL-Server?utm_source=chatgpt.com "What is Microsoft SQL Server? | Definition from TechTarget"
[2]: https://learn.microsoft.com/en-us/sql/database-engine/sql-database-engine?view=sql-server-ver17&utm_source=chatgpt.com "SQL Database Engine - Microsoft SQL | Microsoft Learn"
[3]: https://learn.microsoft.com/en-us/sql/sql-server/connect-to-database-engine?view=sql-server-ver17&utm_source=chatgpt.com "Connect to the SQL Server Database Engine - SQL Server | Microsoft Learn"
