# 🐳 Guia Quickstart de Docker & Containers

> **Academia Java Backend Developer**  
> Ficheiro de referência para criação de imagens OCI, empacotamento multi-stage e execução da API MyMovies em containers.

---

## 📌 Porquê usar Containers?

O **Docker** empacota a aplicação Java, o JRE 21 e todas as configurações necessárias num artefato único e imutável (Imagem Container). Isso garante que o código rode exatamente da mesma forma no ambiente de desenvolvimento, homologação e produção.

---

## 🏗️ 1. Dockerfile Multi-Stage Otimizado

Abaixo está o `Dockerfile` utilizado na **Aula 7**, localizado na raiz do projeto:

```dockerfile
# ----- STAGE 1: Build da Aplicação -----
FROM eclipse-temurin:21-jdk-alpine AS builder
WORKDIR /app
COPY . .
RUN ./mvnw clean package -DskipTests

# ----- STAGE 2: Runtime enxuto e seguro -----
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app

# Criar utilizador não-root para boas práticas de segurança
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser

# Copiar apenas o JAR compilado do Stage 1
COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
```

---

## 🚀 2. Comandos Operacionais

### 1️⃣ Gerar o Artefato JAR Localmente (Pré-requisito se não usar multi-stage)
```bash
./mvnw clean package -DskipTests
```

### 2️⃣ Construir a Imagem Docker
```bash
docker build -t mymovies-api:1.0 .
```

### 3️⃣ Executar o Container
```bash
docker run -d \
  -p 8080:8080 \
  --name mymovies-container \
  -e SPRING_PROFILES_ACTIVE=prod \
  -e TMDB_API_KEY="sua_chave_aqui" \
  mymovies-api:1.0
```

---

## 🔍 3. Comandos Úteis de Diagnóstico

* **Listar containers em execução:**
  ```bash
  docker ps
  ```

* **Visualizar os logs da aplicação dentro do container:**
  ```bash
  docker logs -f mymovies-container
  ```

* **Parar e remover o container:**
  ```bash
  docker stop mymovies-container
  docker rm mymovies-container
  ```

* **Listar imagens locais:**
  ```bash
  docker images
  ```

---

## 🔐 4. Passagem de Segredos e Variáveis de Ambiente

Nunca grave chaves de API ou senhas dentro do `Dockerfile`. Injete as credenciais na execução do container utilizando a flag `-e`:

```bash
docker run -d -p 8080:8080 -e TMDB_API_KEY="SUA_CHAVE_REAL" mymovies-api:1.0
```
