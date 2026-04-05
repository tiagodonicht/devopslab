# 🚀 DevOps Lab — Python/Flask com CI/CD

Aplicação web simples em **Python/Flask** que demonstra na prática um pipeline completo de **DevOps & Cloud**, com integração contínua via **Travis CI**, deploy automático em staging no **Heroku** e deploy em produção no **Google App Engine (GCP)**.

---

## 🏗️ Pipeline CI/CD

O pipeline é orquestrado pelo **Travis CI** e executa 4 estágios automaticamente a cada push na branch `main`:

```
┌─────────────────────────────────────────────────────────────┐
│                        Travis CI                            │
│                                                             │
│  ┌──────────┐   ┌────────────┐   ┌──────────┐   ┌───────┐  │
│  │  Build   │ → │ STG Deploy │ → │ STG Test │ → │ PROD  │  │
│  │  + Tests │   │  (Heroku)  │   │  (curl)  │   │(GCP)  │  │
│  └──────────┘   └────────────┘   └──────────┘   └───────┘  │
└─────────────────────────────────────────────────────────────┘
```

| Estágio | O que faz |
|---|---|
| **Build** | Instala dependências e executa testes unitários com `coverage` |
| **STG Deploy** | Deploy automático no Heroku (ambiente de staging) |
| **STG Test** | Valida a aplicação em staging via `curl` |
| **PROD Deploy** | Deploy no Google App Engine (produção) |

---

## 🛠️ Tecnologias utilizadas

| Tecnologia | Uso |
|---|---|
| Python 3.7.9 | Linguagem da aplicação |
| Flask | Framework web |
| Unittest + Coverage | Testes unitários e cobertura de código |
| Travis CI | Integração e entrega contínua (CI/CD) |
| Heroku | Ambiente de staging |
| Google App Engine | Ambiente de produção (GCP) |
| WSGI | Servidor de aplicação |

---

## 📋 Pré-requisitos

- [Python 3.7+](https://www.python.org/downloads/) instalado
- [pip](https://pip.pypa.io/) instalado

---

## 🚀 Como executar localmente

**1. Clone o repositório:**

```bash
git clone https://github.com/tiagodonicht/devopslab.git
cd devopslab
```

**2. Instale as dependências:**

```bash
pip install flask flask-wtf coverage
```

**3. Execute a aplicação:**

```bash
python app.py
```

A aplicação estará disponível em `http://localhost:5000`.

---

## 🧪 Como executar os testes

```bash
coverage run test.py
coverage report app.py
```

---

## 📡 Endpoints

| Método | Endpoint | Descrição |
|---|---|---|
| `GET` | `/` | Retorna `Hello World` |

---

## 📁 Estrutura do projeto

```
devopslab/
├── app.py                  # Aplicação Flask principal
├── test.py                 # Testes unitários (Unittest)
├── application.wsgi        # Configuração WSGI
├── requirements.txt        # Dependências Python
├── runtime.txt             # Versão do Python (Heroku)
├── Procfile                # Comando de inicialização (Heroku)
├── app.yaml                # Configuração do Google App Engine
├── .travis.yml             # Pipeline CI/CD
├── .gcloudignore           # Arquivos ignorados no deploy GCP
└── .gitignore
```

---

## 🔐 Variáveis de ambiente (CI/CD)

As seguintes variáveis devem estar configuradas no Travis CI:

| Variável | Descrição |
|---|---|
| `HEROKU_API_KEY` | API key do Heroku para deploy em staging |
| `encrypted_7cff072e76ba_key` | Chave de decriptação do service account GCP |
| `encrypted_7cff072e76ba_iv` | IV de decriptação do service account GCP |

> O arquivo de credenciais do GCP (`*.json`) está encriptado com OpenSSL e decriptado automaticamente durante o pipeline.

---

## 🌐 Ambientes

| Ambiente | Plataforma | URL |
|---|---|---|
| Staging | Heroku | `https://devopslab-tiago.herokuapp.com/` |
| Produção | Google App Engine | Projeto `lab-devops-cloud-314123` |

---

## 💡 Sobre o projeto

Este projeto foi desenvolvido como parte do **DevOps Lab** do programa de **Arquitetura de Soluções** da [FIAP](https://www.fiap.com.br/), com foco na aplicação prática de conceitos de integração e entrega contínua (CI/CD), testes automatizados e deploy em múltiplos ambientes de nuvem.

---

## 📄 Licença

Este projeto está licenciado sob a [MIT License](LICENSE).
