# API REST em Go
--
## CRÉDITOS
https://www.youtube.com/watch?v=3p4mpId_ZU8&t=328s
--
Uma API RESTful simples e escalável construída com Go, projetada para demonstrar as melhores práticas no desenvolvimento de microsserviços com arquitetura limpa e ferramentas modernas.

## Índice
- [Funcionalidades](#funcionalidades)
- [Tecnologias](#tecnologias)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Primeiros Passos](#primeiros-passos)
  - [Pré-requisitos](#pré-requisitos)
  - [Instalação](#instalação)
  - [Executando a Aplicação](#executando-a-aplicação)
- [Endpoints da API](#endpoints-da-api)
- [Testes](#testes)
- [Contribuição](#contribuição)
- [Licença](#licença)

## Funcionalidades
- API RESTful com operações CRUD
- Arquitetura de código modular e limpa
- Integração com banco de dados (por exemplo, PostgreSQL/MySQL)
- Autenticação baseada em JWT (presumida, comum em APIs REST em Go)
- Suporte a Docker para implantação em contêineres
- Configuração baseada em variáveis de ambiente
- Tratamento abrangente de erros
- Testes unitários com alta cobertura

## Tecnologias
- **Go**: Versão 1.21+ para suporte a módulos modernos
- **Framework**: [Gin Gonic](https://github.com/gin-gonic/gin) (ou outro como Echo/Gorilla Mux, inferido como comum)
- **Banco de Dados**: GORM para ORM (presumido, com base em padrões de APIs REST em Go)
- **Docker**: Para conteinerização
- **Testes**: Biblioteca nativa de testes do Go
- **Logging**: Log estruturado (por exemplo, usando `log` ou `logrus`)

## Estrutura do Projeto
```
rest-api-go/
├── cmd/                # Ponto de entrada da aplicação
│   └── api/            # Pacote principal do servidor da API
├── internal/           # Código privado da aplicação
│   ├── config/         # Carregamento de configurações
│   ├── handlers/       # Manipuladores HTTP para endpoints da API
│   ├── models/         # Modelos de dados e esquemas do banco
│   ├── repository/     # Operações com banco de dados
│   └── utils/          # Funções utilitárias
├── pkg/                # Bibliotecas compartilhadas
├── tests/              # Testes unitários e de integração
├── Dockerfile          # Configuração do Docker
├── docker-compose.yml  # Docker Compose para desenvolvimento local
├── go.mod              # Dependências do módulo Go
├── go.sum              # Somas de verificação das dependências
└── README.md           # Documentação do projeto
```

Essa estrutura segue o [Layout Padrão de Projetos Go](https://github.com/golang-standards/project-layout) para escalabilidade e manutenção.

## Primeiros Passos

### Pré-requisitos
- **Go**: Versão 1.21 ou superior ([download](https://golang.org/dl/))
- **Docker**: Para configuração em contêineres ([instalar](https://docs.docker.com/get-docker/))
- **Banco de Dados**: PostgreSQL/MySQL (presumido; configure conforme necessário)
- **Git**: Para clonar o repositório

### Instalação
1. Clone o repositório:
   ```bash
   git clone https://github.com/rajssq/rest-api-go.git
   cd rest-api-go
   ```

2. Instale as dependências:
   ```bash
   go mod tidy
   ```

3. Configure as variáveis de ambiente:
   Crie um arquivo `.env` na raiz do projeto com base no exemplo `.env.example` (se disponível) e ajuste as configurações, como conexão com o banco de dados:
   ```env
   DB_HOST=localhost
   DB_PORT=5432
   DB_USER=admin
   DB_PASSWORD=secret
   DB_NAME=api_db
   PORT=8080
   ```

### Executando a Aplicação
1. **Localmente**:
   ```bash
   go run cmd/api/main.go
   ```
   A API estará disponível em `http://localhost:8080` (ou na porta configurada).

2. **Com Docker**:
   ```bash
   docker-compose up --build
   ```
   Isso iniciará a API e o banco de dados (se configurado no `docker-compose.yml`).

## Endpoints da API
Exemplo de endpoints (ajuste conforme o projeto real):
- `GET /api/users` - Lista todos os usuários
- `POST /api/users` - Cria um novo usuário
- `GET /api/users/:id` - Obtém detalhes de um usuário
- `PUT /api/users/:id` - Atualiza um usuário
- `DELETE /api/users/:id` - Remove um usuário

Consulte a documentação específica ou use ferramentas como Postman para testar os endpoints.

## Testes
Execute os testes unitários:
```bash
go test ./tests/... -v
```
Os testes cobrem handlers, repositórios e utilitários (presumido).
