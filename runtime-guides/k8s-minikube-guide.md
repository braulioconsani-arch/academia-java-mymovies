# ☸️ Guia de Orquestração Local com Minikube e kubectl

> **Academia Java Backend Developer**  
> Ficheiro de referência para implantação, gestão de configurações e escalonamento da API MyMovies num cluster Kubernetes local.

---

## 📌 Conceitos Fundamentais do Kubernetes

* **Pod:** A menor unidade implantável no Kubernetes (contém um ou mais containers).
* **Deployment:** Gerencia o ciclo de vida, atualizações e quantidade de réplicas dos Pods.
* **Service:** Expõe os Pods para acesso de rede interno ou externo com balanceamento de carga.
* **ConfigMap / Secret:** Externaliza configurações e dados de ambiente.

---

## 🚀 1. Inicialização do Cluster Local (Minikube)

1. Iniciar o cluster Minikube com o driver Docker:
   ```bash
   minikube start --driver=docker
   ```

2. Verificar o estado do cluster:
   ```bash
   minikube status
   ```

3. Reutilizar o ambiente Docker do Minikube:
   ```bash
   # Linux e macOS
   eval $(minikube docker-env)
   ```

---

## 🔑 2. Gestão de Configurações do Cluster

Antes de aplicar os manifestos da aplicação, crie o objeto de configuração para a chave da API:

```bash
kubectl create secret generic tmdb-config \
  --from-literal=api-key="sua_chave_api"
```

---

## 📜 3. Aplicação dos Manifestos YAML

Os manifestos do Kubernetes estão armazenados na pasta `k8s/` do projeto:

```bash
# Aplicar os manifestos do projeto
kubectl apply -f k8s/
```

---

## 🔍 4. Monitorização e Diagnóstico

```bash
# Listar Pods em execução
kubectl get pods

# Listar Deployments e Services
kubectl get deployments
kubectl get services

# Visualizar logs da aplicação
kubectl logs -f -l app=mymovies
```

---

## 🌐 5. Acessar a Aplicação Implantada

Para obter o endereço do serviço exposto no Minikube:

```bash
minikube service mymovies-service --url
```

Utilize o endereço retornado no **Bruno** para testar as requisições à API.

---

## 📈 6. Escalonamento

```bash
# Escalar a aplicação para 2 réplicas
kubectl scale deployment/mymovies-deployment --replicas=2
```
