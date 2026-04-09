# Projeto Aluno API

Este projeto é uma aplicação Java desenvolvida para demonstrar a integração com banco de dados relacional (Oracle) e o consumo de APIs REST externas. O sistema realiza operações de CRUD para gerenciamento de alunos e consulta serviços públicos para obtenção de dados de endereços e personagens de Star Wars.

## Funcionalidades

O projeto está dividido em dois módulos principais:

### 1. Gerenciamento de Alunos (Banco de Dados)
Integração via JDBC com banco de dados Oracle para manipulação da tabela `T_FIAP_ALUNO`.
* **Inserir**: Cadastro de novos alunos (RM, Nome, Turma, Nota).
* **Atualizar**: Alteração de dados de alunos existentes.
* **Deletar**: Remoção de alunos pelo RM.
* **Selecionar**: Listagem de todos os alunos cadastrados.

### 2. Consumo de APIs Externas (Client HTTP)
Utiliza `Apache HttpClient` e `GSON` para requisições e desserialização de JSON.
* **ViaCEP**: Consulta de endereços através do CEP (`viacep.com.br`).
* **SWAPI (Star Wars API)**: Consulta de dados de personagens da saga Star Wars (`swapi.dev`).

## Tecnologias Utilizadas

* **Java 21**
* **Maven**: Gerenciamento de dependências.
* **Oracle JDBC Driver (`ojdbc11`)**: Conectividade com banco de dados.
* **Apache HttpClient**: Para realização de requisições HTTP (`GET`).
* **Google Gson**: Para conversão de JSON para objetos Java.
* **Java Swing (JOptionPane)**: Para interação simples com o usuário via janelas de diálogo.

## Estrutura do Projeto

* `br.com.fiap.api`: Modelos (DTOs) para as APIs externas (`Endereco`, `Pessoa`).
* `br.com.fiap.beans`: Modelo de domínio (`Aluno`).
* `br.com.fiap.conexoes`: Classe de conexão com o banco de dados (Singleton/Factory).
* `br.com.fiap.dao`: Objeto de Acesso a Dados (DAO) com os métodos SQL.
* `br.com.fiap.services`: Serviços responsáveis por chamar as APIs externas.
* `br.com.fiap.main`: Classes executáveis para testar cada funcionalidade (`TesteInserir`, `TesteViaCep`, etc).

## Como Executar

### Pré-requisitos
* Java JDK 21 instalado.
* Maven instalado.
* Acesso a um banco de dados Oracle (ou alteração da string de conexão).

### Configuração do Banco de Dados
Verifique a classe `ConexaoFactory.java` e certifique-se de que as credenciais e a URL do banco estão corretas para o seu ambiente:

```java
// Exemplo em src/main/java/br/com/fiap/conexoes/ConexaoFactory.java
return DriverManager.getConnection("jdbc:oracle:thin:@oracle.fiap.com.br:1521:orcl", "SEU_USUARIO", "SUA_SENHA");
