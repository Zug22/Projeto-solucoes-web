# EduGestor  
Sistema Web Full Stack de Gestao Escolar (Monorepo)

O **EduGestor** e um sistema completo de gestao escolar desenvolvido em arquitetura monorepo, integrando backend em Flask + MongoDB e frontend em HTML/CSS/JS puro. O projeto inclui funcionalidades para professores e alunos, como autenticacao JWT, dashboards, lancamento de notas, boletins e controle de frequencia.

---

## 📌 Sumario
- [Visao Geral](#visao-geral)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Arquitetura do Projeto](#arquitetura-do-projeto)
- [Instalacao](#instalacao)
- [Execucao-via-runsh](#execucao-via-runsh)
- [Funcionalidades](#funcionalidades)

---

## Visao Geral

O EduGestor foi criado com foco em simplicidade, responsividade e separacao clara de responsabilidades.  
O sistema oferece:

- Interface web responsiva com tema claro e escuro  
- Backend robusto com autenticacao JWT  
- Dashboards separados para Aluno e Professor  
- Banco MongoDB local via PyMongo  
- Orquestracao completa via script `run.sh`

---

## Tecnologias Utilizadas

### Backend
- Python 3.12  
- Flask  
- PyMongo  
- Flask-JWT-Extended  
- Bcrypt  

### Frontend
- HTML5  
- CSS3 (variaveis de tema e modo escuro/claro)  
- JavaScript ES6+ (fetch API e manipulacao de DOM)

### Banco de Dados
- MongoDB em modo Standalone (Systemd)

### Ambiente
- Linux (Ubuntu/Debian)  
- Ambiente virtual `venv`  
- Scripts Bash

---

## Arquitetura do Projeto

/backend
app.py # Entry point Flask
database.py # Conexao Mongo isolada
.env # Variaveis de ambiente
/routes
auth.py
aluno.py
professor.py

/frontend
index.html
/css
/js
/img

run.sh # Script principal de automacao


### Principios adotados
- Separacao clara entre backend e frontend  
- Evita circular imports usando modulo dedicado para conexao  
- Frontend 100% em JS puro

---

## Instalacao

### 1. Clone o repositorio
```bash
git clone https://github.com/seu-usuario/EduGestor.git
cd EduGestor

### 2. Crie o ambiente virtual e instale as dependencias

cd backend
python3.12 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

### 3. Inicie o MongoDB

sudo systemctl enable mongod
sudo systemctl start mongod

### Execucao via run.sh

O script run.sh automatiza toda a execucao do projeto.
O que ele faz automaticamente

    - Encerra processos ocupando as portas 5000 e 5502

    - Inicia o servico do MongoDB

    - Ativa a venv do backend

    - Inicia o backend Flask

    - Inicia o servidor HTTP do frontend

    - Abre o navegador

    - Encerra todos os processos ao finalizar

### Para executar

Na raiz do projeto:

bash run.sh

Se necessario:

chmod +x run.sh
./run.sh
