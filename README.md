# 🎮 Loja de Games - API REST

![Java](https://img.shields.io/badge/Java-21-orange?style=for-the-badge&logo=openjdk)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.x-brightgreen?style=for-the-badge&logo=springboot)
![MySQL](https://img.shields.io/badge/MySQL-8.0-blue?style=for-the-badge&logo=mysql)
![Maven](https://img.shields.io/badge/Maven-Project-red?style=for-the-badge&logo=apachemaven)
![Status](https://img.shields.io/badge/Status-Concluído-success?style=for-the-badge)

## 📌 Sobre o projeto

Este projeto é uma API REST desenvolvida em Java com Spring Boot, criada como atividade prática do módulo de Spring da Generation Brasil.

A aplicação representa o backend de uma Loja de Games, permitindo o gerenciamento de produtos e categorias por meio de operações CRUD.

O sistema permite cadastrar, listar, buscar, atualizar e deletar registros de produtos e categorias. Além disso, os produtos são classificados por categoria, utilizando relacionamento entre entidades.

## 🎯 Objetivo

O objetivo do projeto é praticar os principais conceitos de desenvolvimento backend com Spring Boot, incluindo:

- Criação de projeto Spring com Maven
- Configuração de banco de dados MySQL
- Criação de entidades com JPA
- Organização em camadas
- Implementação de Repository
- Implementação de Controller REST
- Relacionamento entre entidades
- Validação de dados
- Versionamento com Git e GitHub

## 🧱 Estrutura do projeto

O projeto foi organizado seguindo a separação de responsabilidades em camadas:

```txt
src/main/java/com/generation/lojagames
│
├── controller
│   ├── CategoriaController.java
│   └── ProdutoController.java
│
├── model
│   ├── Categoria.java
│   └── Produto.java
│
├── repository
│   ├── CategoriaRepository.java
│   └── ProdutoRepository.java
│
└── LojagamesApplication.java
```

## 📂 Camadas da aplicação

### Model

A camada `model` contém as classes que representam as entidades do sistema e que são mapeadas como tabelas no banco de dados.

Entidades criadas:

- `Categoria`
- `Produto`

### Repository

A camada `repository` contém as interfaces responsáveis pela comunicação com o banco de dados por meio do Spring Data JPA.

Repositories criados:

- `CategoriaRepository`
- `ProdutoRepository`

### Controller

A camada `controller` contém as classes responsáveis por receber as requisições HTTP e devolver as respostas da API.

Controllers criados:

- `CategoriaController`
- `ProdutoController`

## 🗃️ Entidades

### Categoria

A entidade `Categoria` representa a classificação dos produtos da loja.

Principais atributos:

- `id`
- `tipo`
- `descricao`
- `produtos`

### Produto

A entidade `Produto` representa os produtos cadastrados na loja.

Principais atributos:

- `id`
- `nome`
- `descricao`
- `preco`
- `estoque`
- `categoria`

## 🔗 Relacionamento entre entidades

O projeto implementa um relacionamento do tipo **One to Many** e **Many to One**.

Uma categoria pode ter vários produtos, enquanto cada produto pertence a uma única categoria.

Na entidade `Categoria`, foi utilizado:

```java
@OneToMany(mappedBy = "categoria", cascade = CascadeType.ALL)
@JsonIgnoreProperties("categoria")
private List<Produto> produtos;
```

Na entidade `Produto`, foi utilizado:

```java
@ManyToOne
@JsonIgnoreProperties("produtos")
private Categoria categoria;
```

Esse relacionamento permite que os produtos sejam organizados por categoria dentro da aplicação.

## 🚀 Tecnologias utilizadas

- Java 21
- Spring Boot
- Spring Web
- Spring Data JPA
- Bean Validation
- MySQL
- Maven
- Insomnia
- Git
- GitHub
- Spring Tool Suite

## ⚙️ Configuração do banco de dados

O projeto utiliza o banco de dados MySQL.

Banco utilizado:

```sql
CREATE DATABASE db_lojagames;
```

Configuração utilizada no arquivo `application.properties`:

```properties
spring.application.name=lojagames

spring.datasource.url=jdbc:mysql://localhost:3306/db_lojagames?createDatabaseIfNotExist=true&serverTimezone=America/Sao_Paulo&useSSL=false
spring.datasource.username=root
spring.datasource.password=SUA_SENHA_DO_MYSQL

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

## 📡 Endpoints da API

### Categoria

| Método | Endpoint | Descrição |
|---|---|---|
| GET | `/categorias` | Lista todas as categorias |
| GET | `/categorias/{id}` | Busca uma categoria por ID |
| GET | `/categorias/tipo/{tipo}` | Busca categorias por tipo |
| POST | `/categorias` | Cadastra uma nova categoria |
| PUT | `/categorias` | Atualiza uma categoria existente |
| DELETE | `/categorias/{id}` | Deleta uma categoria |

### Produto

| Método | Endpoint | Descrição |
|---|---|---|
| GET | `/produtos` | Lista todos os produtos |
| GET | `/produtos/{id}` | Busca um produto por ID |
| GET | `/produtos/nome/{nome}` | Busca produtos por nome |
| POST | `/produtos` | Cadastra um novo produto |
| PUT | `/produtos` | Atualiza um produto existente |
| DELETE | `/produtos/{id}` | Deleta um produto |

## ✅ Funcionalidades implementadas

- CRUD completo de Categoria
- CRUD completo de Produto
- Relacionamento entre Categoria e Produto
- Validação de campos obrigatórios
- Persistência de dados com MySQL
- Organização em camadas
- API REST com Spring Boot

## 📁 Arquivos principais

### Controllers

- [CategoriaController.java](https://github.com/Day-Barbosa/Loja_Games/blob/main/src/main/java/com/generation/lojagames/controller/CategoriaController.java)
- [ProdutoController.java](https://github.com/Day-Barbosa/Loja_Games/blob/main/src/main/java/com/generation/lojagames/controller/ProdutoController.java)

### Models

- [Categoria.java](https://github.com/Day-Barbosa/Loja_Games/blob/main/src/main/java/com/generation/lojagames/model/Categoria.java)
- [Produto.java](https://github.com/Day-Barbosa/Loja_Games/blob/main/src/main/java/com/generation/lojagames/model/Produto.java)

### Repositories

- [CategoriaRepository.java](https://github.com/Day-Barbosa/Loja_Games/blob/main/src/main/java/com/generation/lojagames/repository/CategoriaRepository.java)
- [ProdutoRepository.java](https://github.com/Day-Barbosa/Loja_Games/blob/main/src/main/java/com/generation/lojagames/repository/ProdutoRepository.java)

## ▶️ Como executar o projeto

Clone o repositório:

```bash
git clone https://github.com/Day-Barbosa/Loja_Games.git
```

Acesse a pasta do projeto:

```bash
cd Loja_Games
```

Abra o projeto no Spring Tool Suite.

Configure a senha do banco de dados no arquivo:

```txt
src/main/resources/application.properties
```

Execute a aplicação pela classe principal:

```txt
LojagamesApplication.java
```

A aplicação será executada em:

```txt
http://localhost:8080
```

## 🤝 Contribuição

Este projeto foi desenvolvido para fins educacionais, mas sugestões de melhoria são bem-vindas.

Para contribuir:

```bash
git clone https://github.com/Day-Barbosa/Loja_Games.git
git checkout -b minha-melhoria
git commit -m "Minha melhoria"
git push origin minha-melhoria
```

## 👩‍💻 Desenvolvedora

Desenvolvido por Dayana Barbosa.

GitHub: [Day-Barbosa](https://github.com/Day-Barbosa)

## 📚 Projeto educacional

Este projeto foi desenvolvido para fins educacionais, com o objetivo de praticar conceitos de desenvolvimento backend com Java, Spring Boot, banco de dados relacional e construção de APIs REST.

## 📄 Licença

Este projeto foi desenvolvido para fins educacionais.
