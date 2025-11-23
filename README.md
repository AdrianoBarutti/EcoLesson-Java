# 🌱 EcoLesson - Sistema de Gestão Educacional

Sistema web desenvolvido em Java Spring Boot para gestão de cursos, alunos, professores e certificados em uma plataforma educacional.

## 📋 Sobre o Projeto

O EcoLesson é uma aplicação completa de gestão educacional que permite:
- Gerenciamento de usuários (alunos e professores)
- Cadastro e gestão de cursos
- Emissão e validação de certificados
- Integração com sistemas de mensageria (Kafka e RabbitMQ)
- Integração com IA generativa (OpenAI)
- Monitoramento de métricas e saúde da aplicação
- Internacionalização (Português/Inglês)

## 🚀 Tecnologias Utilizadas

### Backend
- **Java 17**
- **Spring Boot 3.5.4**
- **Spring Data JPA** - Persistência de dados
- **Spring Security** - Autenticação e autorização
- **Spring AI** - Integração com OpenAI
- **Thymeleaf** - Engine de templates
- **Flyway** - Migrations de banco de dados

### Banco de Dados
- **Oracle Database** - Banco de dados principal

### Mensageria
- **Apache Kafka (Redpanda)** - Sistema de mensageria assíncrona
- **RabbitMQ** - Message broker

### Monitoramento
- **Spring Boot Actuator** - Métricas e monitoramento da aplicação

### Ferramentas
- **Maven** - Gerenciamento de dependências
- **Docker Compose** - Orquestração de serviços (Kafka e RabbitMQ)

## 👥 Integrantes

- **Adriano Barutti** - RM: 556760
- **Vitor Kenzo** - RM: 557245

## 📦 Pré-requisitos

Antes de executar o projeto, certifique-se de ter instalado:

- Java 17 ou superior
- Maven 3.6+
- Oracle Database (ou acesso ao banco Oracle da FIAP)
- Docker e Docker Compose (para serviços de mensageria)

## 🔧 Configuração

### 1. Clone o repositório

```bash
git clone https://github.com/AdrianoBarutti/EcoLesson-Java.git
cd EcoLesson-Java
```

### 2. Configure o banco de dados

Edite o arquivo `src/main/resources/application.properties` e configure as credenciais do Oracle:

```properties
spring.datasource.url=jdbc:oracle:thin:@oracle.fiap.com.br:1521:ORCL
spring.datasource.username=SEU_USUARIO
spring.datasource.password=SUA_SENHA
```

### 3. Configure a chave da API OpenAI (opcional)

Se desejar usar as funcionalidades de IA, configure sua chave da OpenAI:

```properties
spring.ai.openai.api-key=SUA_CHAVE_OPENAI
```

### 4. Inicie os serviços de mensageria

Execute o Docker Compose para iniciar Kafka (Redpanda) e RabbitMQ:

```bash
docker-compose up -d
```

Isso iniciará:
- **Redpanda** (Kafka) na porta `9092`
- **RabbitMQ** na porta `5672` (AMQP) e `15672` (Web Console)

## ▶️ Executando a Aplicação

### Opção 1: Maven Wrapper

```bash
./mvnw spring-boot:run
```

No Windows:
```bash
mvnw.cmd spring-boot:run
```

### Opção 2: Maven

```bash
mvn spring-boot:run
```

### Opção 3: Executar o JAR

```bash
mvn clean package
java -jar target/universidade-fiap-0.0.1-SNAPSHOT.jar
```

A aplicação estará disponível em: **http://localhost:8080**

## 📱 Funcionalidades

### Autenticação e Autorização
- Login com Spring Security
- Diferentes perfis: Aluno e Professor
- Páginas personalizadas por perfil

### Gestão de Cursos
- Cadastro de cursos
- Visualização de cursos disponíveis
- Cursos ministrados por professores

### Certificados
- Emissão de certificados
- Validação de certificados
- Visualização de certificados por aluno

### Mensageria
- Envio de mensagens via Kafka
- Envio de mensagens via RabbitMQ
- Consumo de mensagens assíncronas

### Inteligência Artificial
- Integração com OpenAI
- Geração de mensagens personalizadas
- Análise de conteúdo

### Monitoramento
- Spring Boot Actuator
- Métricas de CPU e memória
- Health checks
- Acesso via `/actuator`

## 🌐 Internacionalização

A aplicação suporta dois idiomas:
- **Português** (padrão)
- **Inglês**

Os arquivos de mensagens estão em:
- `src/main/resources/mensagens_pt.properties`
- `src/main/resources/mensagens_en.properties`

## 📊 Estrutura do Banco de Dados

O banco de dados possui as seguintes tabelas principais:
- `T_USUARIOS` - Usuários do sistema
- `T_CURSO` - Cursos cadastrados
- `T_CERTIFICADO` - Certificados emitidos
- `FUNCAO` - Funções/perfis dos usuários
- `USUARIO_FUNCAO_TAB` - Relação Many-to-Many entre usuários e funções

As migrations do Flyway estão em: `src/main/resources/db/migration/`

## 🔐 Segurança

- Autenticação baseada em Spring Security
- Senhas criptografadas
- Controle de acesso baseado em roles (ROLE_ALUNO, ROLE_PROFESSOR)
- Proteção CSRF habilitada

## 📝 Endpoints Principais

- `/` - Página inicial (redireciona conforme perfil)
- `/login` - Página de login
- `/curso` - Gestão de cursos
- `/certificado` - Gestão de certificados
- `/usuario` - Gestão de usuários
- `/kafka/mensagem` - Envio de mensagens via Kafka
- `/rabbit/mensagem` - Envio de mensagens via RabbitMQ
- `/ia/mensagem` - Funcionalidades de IA
- `/actuator` - Endpoints de monitoramento

## 🛠️ Desenvolvimento

### Executar testes

```bash
mvn test
```

### Build do projeto

```bash
mvn clean package
```

## 📄 Licença

Este projeto foi desenvolvido como parte do curso da FIAP.

## 🤝 Contribuindo

Este é um projeto acadêmico desenvolvido pelos integrantes listados acima.

---

**Desenvolvido com ❤️ por Adriano Barutti e Vitor Kenzo**

