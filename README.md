Auth Service
Este é um serviço de autenticação desenvolvido com Spring Boot e Spring Security, utilizando JWT (JSON Web Token) para autenticação stateless. O serviço permite o registro de novos usuários e o login para geração de tokens JWT.

Tecnologias Utilizadas
Spring Boot 3.1.5

Spring Security

JWT (JSON Web Token)

Spring Data JPA

MySQL (ou outro banco de dados compatível)

Lombok (para reduzir boilerplate code)

Spring Boot DevTools (para desenvolvimento)

Funcionalidades
Registro de Usuários:

Endpoint para registrar novos usuários com nome de usuário e senha.

A senha é codificada usando BCryptPasswordEncoder.

Login e Geração de Token JWT:

Endpoint para autenticação de usuários.

Retorna um token JWT válido por 10 horas.

Autenticação Stateless:

Utiliza JWT para autenticação, sem necessidade de sessões no servidor.

Configuração de Segurança:

Configuração personalizada do Spring Security para permitir acesso público aos endpoints de registro e login.

Todos os outros endpoints exigem autenticação via token JWT.

Como Executar o Projeto
Pré-requisitos
Java 17 (ou superior)

MySQL (ou outro banco de dados compatível)

Maven (para gerenciamento de dependências)

Passos para Configuração
Clone o Repositório:

bash
Copy
git clone https://github.com/seu-usuario/auth-service.git
cd auth-service
Configure o Banco de Dados:

Crie um banco de dados MySQL chamado auth_service (ou outro nome de sua preferência).

Atualize o arquivo application.properties com as credenciais do banco de dados:

properties
Copy
spring.datasource.url=jdbc:mysql://localhost:3306/auth_service
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.jpa.hibernate.ddl-auto=update
Compile o Projeto:

bash
Copy
mvn clean install
Execute a Aplicação:

bash
Copy
mvn spring-boot:run
Acesse a Aplicação:

A aplicação estará disponível em http://localhost:8080.

Endpoints da API
1. Registrar Usuário
Método: POST

URL: /auth/register

Corpo da Requisição:

json
Copy
{
  "username": "usuario",
  "password": "senha123"
}
Resposta de Sucesso:

json
Copy
"Usuário registrado com sucesso!"
2. Login e Gerar Token JWT
Método: POST

URL: /auth/login

Corpo da Requisição:

json
Copy
{
  "username": "usuario",
  "password": "senha123"
}
Resposta de Sucesso:

json
Copy
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
Estrutura do Projeto
Copy
src/main/java/com/seuapp/
├── config/               # Configurações do Spring Security e JWT
│   ├── JwtUtil.java
│   └── SecurityConfig.java
├── controller/           # Controladores da API
│   └── AuthController.java
├── dto/                  # Objetos de Transferência de Dados (DTOs)
│   ├── AuthRequest.java
│   └── AuthResponse.java
├── model/                # Entidades JPA
│   └── User.java
├── repository/           # Repositórios Spring Data JPA
│   └── UserRepository.java
├── service/              # Lógica de negócios
│   ├── CustomUserDetailsService.java
│   └── UserService.java
└── AuthServiceApplication.java # Classe principal da aplicação
Testando a Aplicação
1. Registrar um Usuário
Use o seguinte comando curl para registrar um novo usuário:

bash
Copy
curl -X POST http://localhost:8080/auth/register \
-H "Content-Type: application/json" \
-d '{"username": "usuario", "password": "senha123"}'
2. Fazer Login e Gerar Token JWT
Use o seguinte comando curl para fazer login e obter o token JWT:

bash
Copy
curl -X POST http://localhost:8080/auth/login \
-H "Content-Type: application/json" \
-d '{"username": "usuario", "password": "senha123"}'
3. Acessar Endpoints Protegidos
Para acessar endpoints protegidos, inclua o token JWT no cabeçalho Authorization:

bash
Copy
curl -X GET http://localhost:8080/endpoint-protegido \
-H "Authorization: Bearer <seu_token_jwt>"
Configurações Adicionais
Logs
Para depuração, habilite logs detalhados no application.properties:

properties
Copy
logging.level.org.springframework.security=DEBUG
logging.level.com.seuapp=DEBUG
Banco de Dados
Se preferir usar outro banco de dados, atualize as configurações no application.properties.

Contribuição
Contribuições são bem-vindas! Siga os passos abaixo:

Faça um fork do projeto.

Crie uma branch para sua feature (git checkout -b feature/nova-feature).

Commit suas mudanças (git commit -m 'Adicionando nova feature').

Push para a branch (git push origin feature/nova-feature).

Abra um Pull Request.
