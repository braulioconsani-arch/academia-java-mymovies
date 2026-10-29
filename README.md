# 🎬 Academia Java Backend Developer — MyMovies API

> **Projeto Transversal de Aprendizagem Prática**  
> Aplicação evolutiva desenvolvida durante o curso **Java Backend com Spring Boot** (Java 21 & Spring Boot 4.1.x).

---

## 📌 Sobre o Projeto

O **MyMovies** é um catálogo pessoal de filmes enriquecido com a integração da API externa do **TMDB (The Movie Database)**. A aplicação é construída incrementalmente ao longo de 8 aulas de 3h30, cobrindo desde a exposição de endpoints REST até ao empacotamento em containers e implantação num cluster Kubernetes local (Minikube).

### 🛠️ Stack Tecnológica
* **Linguagem:** Java 21
* **Framework Principal:** Spring Boot 4.1.x (Spring Web, Data JPA, Security, Actuator)
* **Gerenciador de Build:** Maven / Maven Wrapper (`./mvnw`)
* **Persistência:** H2 Database (em memória) / JPA & Hibernate
* **Testes & Qualidade:** JUnit 5, Mockito, TestContainers
* **Cliente HTTP:** Bruno
* **Containers & Runtime:** Docker & Minikube (Kubernetes local)

---

## 🚀 Como Começar (Setup Inicial)

### Pré-requisitos Mínimos
1. **JDK 21** instalado e configurado nas variáveis de ambiente (`JAVA_HOME`).
2. **IntelliJ IDEA** (Community ou Ultimate).
3. **Bruno** (Cliente HTTP para testes das APIs).

---

### ⬇️ Obtendo o Código do Projeto

Escolha a modalidade que melhor se adapta ao seu nível de conhecimento em versionamento:

#### 🔹 Opção A: Para quem já usa Git / GitHub (Recomendado)
1. Faça um **Fork** deste repositório para a sua conta pessoal no GitHub.
2. Clone o seu fork na sua máquina local:
   ```bash
   git clone https://github.com/SEU_USUARIO/academia-java-mymovies.git
   cd academia-java-mymovies
   ```
3. Adicione o repositório oficial do professor como `upstream` para receber atualizações e correções:
   ```bash
   git remote add upstream https://github.com/NOME_PROFESSOR/academia-java-mymovies.git
   ```

#### 🔹 Opção B: Para quem não utiliza Git
1. No topo desta página do GitHub, clique no botão verde **Code > Download ZIP**.
2. Descompacte o arquivo numa pasta local (ex: `~/projetos/academia-java-mymovies`).
3. Abra a pasta diretamente no **IntelliJ IDEA**.

---

## ⚙️ Executando a Aplicação

### Pelo IntelliJ IDEA
1. Abra a pasta do projeto no IntelliJ IDEA (`File > Open`).
2. Aguarde o IntelliJ importar as dependências declaradas no `pom.xml`.
3. Localize e execute a classe principal:  
   `src/main/java/com/academia/mymovies/MyMoviesApplication.java`.
4. Confirme nos logs do console a mensagem: `Started MyMoviesApplication on port 8080`.

### Pela Linha de Comando (Maven Wrapper)
```bash
# Executar a aplicação Spring Boot
./mvnw spring-boot:run

# Compilar e executar os testes unitários
./mvnw test
```

---

## 🧪 Testando os Endpoints (Bruno)

Dentro do repositório, consulte a pasta **`http/`**. Ela contém as coleções HTTP pré-configuradas para o **Bruno**:

1. Abra o **Bruno**.
2. Importe a pasta `http/` do projeto.
3. Selecione a requisição referente à aula atual (ex: `GET http://localhost:8080/api/movies`) e clique em **Send**.

---

## 📍 Checkpoints & Soluções das Aulas

O código da aplicação avança aula a aula. A branch `main` representa sempre o estado integrado mais recente. As soluções oficiais de cada aula estão marcadas no repositório através de **Tags de Checkpoint**:

| Aula | Tópico Central | Tag de Checkpoint da Solução |
| :--- | :--- | :--- |
| **Aula 1** | Spring Boot & REST Básico | `checkpoint/aula-01-rest` |
| **Aula 2** | API Design, DTOs & Validation | `checkpoint/aula-02-api-design` |
| **Aula 3** | Persistência com JPA/Hibernate | `checkpoint/aula-03-jpa` |
| **Aula 4** | Integração Externa (TMDB) | `checkpoint/aula-04-tmdb` |
| **Aula 5** | Qualidade, Erros e Testes | `checkpoint/aula-05-quality` |
| **Aula 6** | Security, JWT e OAuth2 | `checkpoint/aula-06-security` |
| **Aula 7** | Empacotamento JAR e Container | `checkpoint/aula-07-deployable` |
| **Aula 8** | Kubernetes Local (Minikube) | `checkpoint/aula-08-final` |

### Como carregar a solução oficial de uma aula específica:

* **Via Git:**
  ```bash
  # Baixar as tags do repositório do professor
  git fetch upstream --tags

  # Alternar para a tag desejada
  git checkout checkpoint/aula-01-rest
  ```
* **Via Download (Sem Git):**
  Acesse a aba **Releases / Tags** na página do repositório no GitHub, selecione a Tag desejada (ex: `checkpoint/aula-01-rest`) e faça o download em formato ZIP.

---

## 📂 Estrutura Base do Repositório

```text
academia-java-mymovies/
├── pom.xml                 # Arquivo de configuração de dependências do Maven
├── Dockerfile              # Receita para geração do container OCI da API (Aula 7)
├── src/
│   ├── main/java/          # Código-fonte da aplicação Spring Boot
│   └── main/resources/     # Configurações (application.yml, scripts SQL)
├── http/                   # Arquivos de requisição HTTP para o Bruno / IntelliJ
├── docs/                   # Atividades práticas, materiais de apoio
├── runtime/                   # Guias básicos das ferramentas utilizadas ao longo do curso 
└── k8s/                    # Manifestos de Deployment e Service do Kubernetes (Aula 8)
```

---

## 🔒 Política de Segurança e Segredos

⚠️ **Atenção:** Nunca faça commit de senhas, chaves de API reais (ex: TMDB Token) ou arquivos de ambiente com segredos no Git. Utilize variáveis de ambiente para injetar credenciais sensíveis em tempo de execução.

---
*Academia Java Backend Developer • Guia de Operação Prática*
