# 🔄 ToggleMaster - GitOps (ArgoCD + Kubernetes)

![Kubernetes](https://img.shields.io/badge/Kubernetes-Deploy-blue)
![ArgoCD](https://img.shields.io/badge/ArgoCD-GitOps-purple)
![DevOps](https://img.shields.io/badge/DevOps-Automation-green)
![AWS](https://img.shields.io/badge/AWS-EKS-orange)

---

## 📖 Visão Geral

Este repositório contém a configuração de **GitOps** do projeto ToggleMaster, responsável por gerenciar o deploy dos microsserviços no cluster Kubernetes (EKS) utilizando **ArgoCD**.

O GitOps garante que o estado do cluster esteja sempre sincronizado com o que está definido neste repositório.

---

## 🎯 Objetivo

- Eliminar deploy manual com `kubectl`
- Centralizar o estado desejado das aplicações
- Garantir versionamento das configurações Kubernetes
- Automatizar deploys com base em mudanças no Git

---

## 🏗️ Arquitetura GitOps

Fluxo:

1. Código atualizado nos microsserviços
2. Pipeline CI gera imagem Docker
3. Imagem enviada para o ECR
4. Pipeline atualiza este repositório
5. ArgoCD detecta a mudança
6. ArgoCD sincroniza automaticamente com o cluster

---

## 📂 Estrutura do Projeto

```bash
.
├── apps/
│   ├── auth-service/
│   │   └── deployment.yaml
│   ├── flag-service/
│   │   └── deployment.yaml
│   ├── targeting-service/
│   │   └── deployment.yaml
│   ├── evaluation-service/
│   │   └── deployment.yaml
│   └── analytics-service/
│       └── deployment.yaml
│
├── platform/
│   ├── argocd/
│   └── external-secrets/
│
└── README.md
```

---

## ☸️ Aplicações

- auth-service
- flag-service
- targeting-service
- evaluation-service
- analytics-service

---

## 🚀 Como Funciona o Deploy

### ❌ Manual (não utilizado)
```bash
kubectl apply -f deployment.yaml
```

### ✅ GitOps

1. Pipeline atualiza imagem:
```yaml
image: auth-service:abc123
```

2. Commit neste repositório  
3. ArgoCD detecta  
4. ArgoCD aplica no cluster  

---

## ⚙️ ArgoCD

Responsável por:

- Monitorar o repositório
- Detectar mudanças
- Sincronizar com Kubernetes
- Garantir consistência

---

## 🔐 Segredos

Utiliza **External Secrets** com AWS Secrets Manager:

- Nenhum segredo no Git
- Integração segura com Kubernetes

---

## 🔗 Integração

Infraestrutura:

https://github.com/wilckg/toggle-master-micro-v2

---

## 🔐 Segurança

- Deploy via Git
- Sem acesso direto ao cluster
- Secrets fora do código

---

## ⚠️ Observações

- Não alterar recursos manualmente
- Sempre usar Git
- ArgoCD deve estar com auto-sync

---

## 🧪 Ambientes

Preparado para:

- dev
- staging
- production

---

## 👨‍💻 Autor

Wilck Gomes

---

## 📄 Licença

Projeto educacional (Tech Challenge - FIAP)