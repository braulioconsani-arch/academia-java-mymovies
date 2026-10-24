# 🛠️ Guia de Maven Wrapper e Java 21

> **Academia Java Backend Developer**  
> Ficheiro de referência para compilação, execução, testes e empacotamento da aplicação Spring Boot.

---

## 📌 O que é o Maven e o Maven Wrapper?

O **Apache Maven** é o gerenciador de dependências e automação de build do projeto Java.  
O **Maven Wrapper (`./mvnw`)** é um script distribuído junto com o código-fonte que garante que todos os alunos e o servidor de CI/CD utilizem exatamente a mesma versão do Maven, sem necessidade de instalação manual no sistema operacional.

---

## ☕ 1. Verificação do Ambiente Java 21

Antes de executar qualquer comando, confirme que a versão do Java ativa no seu terminal é a **21**:

```bash
java -version
```

*Saída esperada:* `openjdk version "21.0.x"` ou `java version "21.0.x"`.

---

## 🚀 2. Comandos Essenciais do Maven Wrapper

Execute os comandos a partir da raiz do projeto (`academia-java-mymovies`):

### 🔹 Subir a Aplicação em Modo Desenvolvimento
```bash
# No Linux/macOS:
./mvnw spring-boot:run

# No Windows (CMD/PowerShell):
.\mvnw.cmd spring-boot:run
```

### 🔹 Compilar o Projeto
```bash
./mvnw clean compile
```

### 🔹 Executar a Suíte de Testes Automatizados (JUnit 5 & MockMvc)
```bash
./mvnw test
```

### 🔹 Gerar o Executable JAR (Empacotamento para Produção)
```bash
./mvnw clean package -DskipTests
```
*O ficheiro `.jar` compilado será gerado na pasta `target/` (ex: `target/mymovies-0.0.1-SNAPSHOT.jar`).*

---

## 📄 3. Anatomia do `pom.xml`

O ficheiro `pom.xml` (Project Object Model) concentra as configurações do projeto:

* **`<java.version>21</java.version>`:** Define o nível de linguagem Java.
* **`<parent>`:** Herda as configurações padrões e versões compatíveis do **Spring Boot 4.1.x**.
* **`<dependencies>`:** Lista as bibliotecas do ecossistema:
  * `spring-boot-starter-web`: Suporte a REST e servidor Tomcat embutido.
  * `spring-boot-starter-data-jpa`: Integração com banco de dados via JPA/Hibernate.
  * `spring-boot-starter-validation`: Anotações de validação (`@NotNull`, `@NotBlank`).
  * `spring-boot-starter-security`: Módulo de autenticação e autorização.
  * `spring-boot-starter-test`: Suporte a JUnit 5, Mockito e MockMvc.

---

## 🧹 4. Resolução de Problemas Comuns

* **Erro "Permission denied" ao executar `./mvnw` no Linux/macOS:**
  ```bash
  chmod +x mvnw
  ```
* **Limpar cache do build em caso de comportamento estranho:**
  ```bash
  ./mvnw clean
  ```
