# DSMovie - Projeto de Filmes e Avaliações

Este é um projeto de **filmes e avaliações de filmes**. O sistema permite a visualização de dados dos filmes de forma pública (não requer login). No entanto, a alteração de filmes (inserir, atualizar e deletar) é permitida apenas para usuários com perfil **ADMIN**. As avaliações de filmes podem ser registradas por qualquer usuário logado, seja **CLIENT** ou **ADMIN**.

A entidade **Score** armazena a nota (de 0 a 5) que cada usuário atribui a cada filme. Sempre que um usuário registra uma nota, o sistema calcula a média das notas de todos os usuários e armazena essa média na entidade **Movie**, juntamente com a contagem de votos.

## Competências Avaliadas

- **Testes unitários em projeto Spring Boot com Java**
- **Implementação de testes unitários com JUnit e Mockito**
- **Cobertura de código com Jacoco**
  
## Funcionalidades

- **Visualização Pública**: Qualquer pessoa pode visualizar os filmes e suas informações sem a necessidade de login.
- **Cadastro e Edição**: Usuários **ADMIN** podem inserir, atualizar ou deletar filmes.
- **Avaliação de Filmes**: Usuários logados (**CLIENT** ou **ADMIN**) podem avaliar filmes com uma nota de 0 a 5.
- **Média de Avaliação**: Sempre que um usuário registra uma avaliação, o sistema recalcula a média das notas e armazena essa informação junto com a contagem de votos.

## Funcionalidades do Sistema

- **Entidade Movie**: Representa um filme no sistema.
- **Entidade Score**: Representa a avaliação de um filme por um usuário.
- **Entidade User**: Representa um usuário, podendo ser **CLIENT** ou **ADMIN**.
- **Autenticação**: Usuários podem se autenticar para registrar avaliações.

## Requisitos do Projeto

- **Acesso público** para visualização dos dados dos filmes.
- **Administração**: Apenas usuários **ADMIN** podem inserir, atualizar ou excluir filmes.
- **Avaliação**: Usuários logados podem avaliar filmes com uma nota de 0 a 5.

## Testes Unitários

### MovieServiceTests

- **findAllShouldReturnPagedMovieDTO**: Testa a listagem paginada de filmes.
- **findByIdShouldReturnMovieDTOWhenIdExists**: Testa a busca de um filme por ID quando o filme existe.
- **findByIdShouldThrowResourceNotFoundExceptionWhenIdDoesNotExist**: Testa a busca de um filme por ID quando o filme não existe.
- **insertShouldReturnMovieDTO**: Testa a inserção de um novo filme.
- **updateShouldReturnMovieDTOWhenIdExists**: Testa a atualização de um filme existente.
- **updateShouldThrowResourceNotFoundExceptionWhenIdDoesNotExist**: Testa a atualização de um filme inexistente.
- **deleteShouldDoNothingWhenIdExists**: Testa a exclusão de um filme existente.
- **deleteShouldThrowResourceNotFoundExceptionWhenIdDoesNotExist**: Testa a exclusão de um filme inexistente.
- **deleteShouldThrowDatabaseExceptionWhenDependentId**: Testa a exclusão de um filme com dependências no banco de dados.

### ScoreServiceTests

- **saveScoreShouldReturnMovieDTO**: Testa a gravação de uma avaliação de filme.
- **saveScoreShouldThrowResourceNotFoundExceptionWhenNonExistingMovieId**: Testa a gravação de uma avaliação para um filme inexistente.

### UserServiceTests

- **authenticatedShouldReturnUserEntityWhenUserExists**: Testa a autenticação de um usuário existente.
- **authenticatedShouldThrowUsernameNotFoundExceptionWhenUserDoesNotExists**: Testa a autenticação de um usuário inexistente.
- **loadUserByUsernameShouldReturnUserDetailsWhenUserExists**: Testa o carregamento de detalhes de um usuário existente.
- **loadUserByUsernameShouldThrowUsernameNotFoundExceptionWhenUserDoesNotExists**: Testa o carregamento de detalhes de um usuário inexistente.

## Tecnologias Usadas

- **Java 17**
- **Spring Boot** para a criação da API RESTful.
- **Spring Security** para gerenciamento de autenticação e autorização.
- **JUnit 5** para testes unitários.
- **Mockito** para mocks nos testes.
- **Jacoco** para cobertura de testes.
- **H2 Database** para banco de dados em memória durante os testes.
