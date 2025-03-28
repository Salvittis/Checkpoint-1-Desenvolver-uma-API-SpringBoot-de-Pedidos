# Checkpoint 1 - API de Pedidos com Spring Boot

**Nome:** Pedro Henrique Salvitti Habiro (RM: 88166)  
**Disciplina:** Arquitetura SOA e Web Services

## 📋 Descrição

API REST para gerenciamento de pedidos desenvolvida com Spring Boot, implementando operações CRUD com validações de negócio. Integra banco de dados H2 em memória para desenvolvimento e testes.

## 🛠 Tecnologias

- **Java 17**
- **Spring Boot 3.1.5**
  - Spring Web
  - Spring Data JPA
  - Lombok
- **H2 Database**
- **Maven**

## 🚀 Como Executar

### Passos:
1. Clone o repositório:
   ```bash
   git clone https://github.com/zzhyyy-dev/cp1_java.git

2. Instale e execute:
    mvn clean install
    mvn spring-boot:run

3. Acesse o console H2:
    http://localhost:8080/h2-console
    JDBC URL: jdbc:h2:mem:checkpoint1
    User: sa
    Password: (vazio)

4. Endpoints
    Base URL: http://localhost:8080/pedidos

    Método	Endpoint	    Descrição	          Validações
    POST	  /pedidos	    Cria novo pedido	  clienteNome: obrigatório
    GET	    /pedidos	    Lista todos pedidos	valorTotal: ≥ 0
    GET	    /pedidos/{id}	Busca pedido por ID	
    PUT	    /pedidos/{id}	Atualiza pedido	
    DELETE	/pedidos/{id}	Remove pedido	

5. Exemplos
    POST /pedidos
    Request:
      {
          "clienteNome": "Maria Silva",
          "valorTotal": 150.50
      }
    Response (201):
      {
          "id": 1,
          "clienteNome": "Maria Silva",
          "dataPedido": "2023-11-20",
          "valorTotal": 150.50
      }

    GET /pedidos
    Response (200 OK)
    {
      "id": 1,
      "clienteNome": "João da Silva",
      "dataPedido": "2023-10-05",
      "valorTotal": 199.99
    }

    GET /pedidos/{id}
      Busca por ID
     Response (200 OK)
    {
      "id": 1,
      "clienteNome": "João da Silva",
      "dataPedido": "2023-10-05",
      "valorTotal": 199.99
    }

    PUT /pedidos/{id}
    Atualização de Pedido
    Request
    {
      "clienteNome": "Maria Oliveira",
      "valorTotal": 150.0
    }

    DELETE /pedidos/{id}
    Exclusão de Pedido
    Response: 204 No Content

// Response (200 OK)
{
  "id": 1,
  "clienteNome": "Maria Oliveira",
  "dataPedido": "2023-10-05",
  "valorTotal": 150.0
}

  Erros comuns
    400 Bad Request:
    {
        "timestamp": "2023-11-20T12:00:00.000Z",
        "status": 400,
        "error": "Bad Request",
        "message": "O nome do cliente é obrigatório"
    }

6. Estrutura do Código
    src/
    ├── main/
    │   ├── java/br/com/fiap/checkpoint1/
    │   │   ├── controller/PedidoController.java
    │   │   ├── model/Pedido.java
    │   │   ├── repository/PedidoRepository.java
    │   │   └── service/PedidoService.java
    │   └── resources/
    │       └── application.properties

7. Este README.md unificado contém:
    - Todas as informações técnicas
    - Guia de execução passo a passo
    - Documentação completa dos endpoints
    - Exemplos práticos
    - Solução de problemas comuns
    - Estrutura do projeto
    - Configurações essenciais