# Cliente API - 9SOAT Tech Challenge FIAP

API responsável pelo gerenciamento de clientes no ecossistema de microserviços do sistema de autoatendimento para lanchonetes.

---

## Sumário

- [Visão Geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Arquitetura](#arquitetura)
- [Requisitos](#requisitos)
- [Como Executar Localmente](#como-executar-localmente)
- [Variáveis de Ambiente](#variáveis-de-ambiente)
- [Testes](#testes)
- [Deploy e Operação](#deploy-e-operação)
- [Documentação da API](#documentação-da-api)
- [Contribuição](#contribuição)
- [Licença](#licença)

---

## Visão Geral

A **Cliente API** é um microserviço desenvolvido em C# (.NET 8), responsável pelo cadastro, consulta, atualização e exclusão de clientes. Faz parte da solução de autoatendimento para lanchonetes, integrando-se com outros microserviços como pedidos, produtos e pagamentos.

---

## Funcionalidades

- Cadastro de clientes (POST /Cliente)
- Consulta de clientes por ID ou CPF (GET /Cliente/{id}, GET /Cliente/cpf/{cpf})
- Atualização de dados cadastrais (PUT /Cliente/{id})
- Exclusão de clientes (DELETE /Cliente/{id})
- Listagem de clientes (GET /Cliente)

---

## Arquitetura

- **Padrão:** Clean Architecture
- **Camadas:**
  - Presentation: Controllers e endpoints da API
  - Application: Regras de negócio e casos de uso
  - Domain: Entidades e contratos
  - Infrastructure: Persistência e integrações externas
- **Banco de Dados:** AWS RDS (SQL)
- **Deploy:** AWS EKS (Kubernetes), CI/CD via GitHub Actions

---

## Requisitos

- [.NET 8 SDK](https://dotnet.microsoft.com/download)
- [Visual Studio 2022](https://visualstudio.microsoft.com/)
- Instância do banco de dados AWS RDS configurada
- Docker (opcional, para execução em container)
- Acesso à AWS (para deploy em nuvem)

---

## Como Executar Localmente

1. **Clone o repositório:**

```bash
   git clone https://github.com/gisele-cesar/tech-challenge-fiap-api-clientes.git
   cd tech-challenge-fiap
```

2. **Configure as variáveis de ambiente** (ver seção abaixo).

3. **Inicie o banco de dados** (AWS RDS ou local).

4. **Abra o projeto no Visual Studio 2022** e selecione `fiap.API` como projeto de inicialização.

5. **Execute a aplicação (F5)**.

6. **Acesse a documentação Swagger:**
   
   Abra o navegador e acesse https://localhost:44322/swagger/index.html para acessar a interface do Swagger e testar as APIs.

---

## Variáveis de Ambiente

Configure as seguintes variáveis no ambiente ou no arquivo `appsettings.Development.json`:

- `ConnectionStrings:DefaultConnection` - String de conexão com o banco de dados
- `Jwt:Key` - Chave para autenticação JWT (se aplicável)
- `AWS:AccessKey` e `AWS:SecretKey` - Credenciais AWS (se necessário)
- Outras variáveis sensíveis devem ser armazenadas no AWS Secrets Manager

---

## Testes

- Execute os testes unitários e de integração com:

```bash
   dotnet test
```

- Os testes estão localizados em `src/Tests/fiap.Tests`.

---

## Deploy e Operação

- **Build da imagem Docker:**

```bash
   docker build -t fiap-api-clientes .
```

- **Deploy no Kubernetes (AWS EKS):**
  - Utilize os manifests em `k8s/` para criar os recursos necessários.
  - O pipeline CI/CD está configurado via GitHub Actions (`deploy.yml`).

---

## Documentação da API

Acesse a documentação interativa via Swagger após iniciar a aplicação:

```bash
   https://localhost:44322/swagger/index.html
```

---

## Contribuição

Contribuições são bem-vindas! Siga as etapas:

1. Fork este repositório
2. Crie uma branch (`git checkout -b feature/nova-funcionalidade`)
3. Commit suas alterações (`git commit -am 'feat: nova funcionalidade'`)
4. Push para a branch (`git push origin feature/nova-funcionalidade`)
5. Abra um Pull Request

---

## Licença

Este projeto está licenciado sob a licença MIT.

---

## Recursos Adicionais

- [Desenho Arquitetura](docs/Desenho%20Arquitetura.jpg)
- [Demonstração em vídeo](https://www.youtube.com/watch?v=A6mOvoZ_910)