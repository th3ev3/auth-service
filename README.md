Auth Service API

Este é um serviço de autenticação desenvolvido com Spring Boot e Spring Security, utilizando JWT (JSON Web Token) para fornecer autenticação sem estado (stateless). A API permite que usuários se registrem e façam login para obter um token JWT, que é utilizado para autenticação em requisições subsequentes.

Funcionalidades

Registro de Usuário: Permite que novos usuários se registrem com um nome de usuário e senha.
Login e Geração de Token JWT: Após o login, o usuário recebe um token JWT que pode ser usado para autenticação em futuros acessos.
Autenticação Stateless: Utiliza JWT para autenticação, sem a necessidade de manter sessões no servidor.
Segurança com Spring Security: Configuração personalizada para proteger os endpoints da API e permitir apenas o acesso autenticado, exceto para os endpoints de registro e login.

Tecnologias Utilizadas

Spring Boot 3.1.5
Spring Security
JWT (JSON Web Token)
Spring Data JPA
MySQL (ou outro banco de dados relacional)
Lombok
Spring Boot DevTools (para desenvolvimento)

Endpoints da API

/auth/register (POST): Endpoint para registrar um novo usuário.
/auth/login (POST): Endpoint para fazer login e obter um token JWT.
/endpoint-protegido (GET): Endpoint protegido, acessível apenas com um token JWT válido.
