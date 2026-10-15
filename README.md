# 🏫 Sistema de Gestão Escolar

Sistema web desenvolvido para gerenciar informações e operações administrativas de uma instituição de ensino, incluindo alunos, professores, cursos, turmas, matrículas e registros de frequência.

O projeto foi desenvolvido com **Python e Flask** no back-end, **MySQL** para persistência de dados e tecnologias web no front-end. A aplicação utiliza rotas para processar requisições, módulos Python para organizar operações relacionadas às entidades e templates HTML para apresentar os dados ao usuário.

## 🛠️ Tecnologias utilizadas

- **Python** — implementação da lógica de aplicação e das operações de negócio.
- **Flask** — criação do servidor web, definição de rotas e processamento de requisições HTTP.
- **MySQL** — armazenamento e relacionamento dos dados escolares.
- **MySQL Connector/Python** — conexão e execução de operações no banco de dados.
- **HTML5** — estruturação das páginas.
- **JavaScript** — interações dinâmicas e envio de requisições assíncronas.
- **Tailwind CSS** — estilização da interface.
- **Flowbite e Heroicons** — componentes visuais e ícones da interface.
- **Node.js e npm** — gerenciamento das dependências utilizadas no processo de estilização.

## ⚙️ Funcionalidades

O sistema possui módulos voltados à gestão dos seguintes registros:

- **Secretarias:** cadastro, consulta, edição e exclusão.
- **Pessoas:** cadastro, pesquisa e atualização de informações.
- **Alunos:** cadastro, pesquisa, edição e exclusão.
- **Professores:** cadastro, pesquisa, edição e exclusão.
- **Cursos:** cadastro, pesquisa, edição e exclusão.
- **Inscrições:** registro, pesquisa e atualização.
- **Turmas:** cadastro, pesquisa, edição e exclusão.
- **Turmas e professores:** associação e gerenciamento de vínculos.
- **Matrículas:** registro, pesquisa, edição e exclusão.
- **Planos de aula:** cadastro, pesquisa, edição e exclusão.
- **Faltas:** registro, pesquisa, edição e exclusão.

## 🏗️ Como o projeto foi desenvolvido

### 1. Back-end com Flask

O arquivo `app.py` concentra a configuração da aplicação Flask e define as rotas responsáveis por atender às solicitações do usuário.

As rotas recebem requisições HTTP, identificam a operação solicitada, acionam funções dos módulos correspondentes e retornam páginas HTML ou respostas JSON, conforme a necessidade.

O sistema utiliza os métodos GET e POST para carregar páginas, processar formulários e executar operações de cadastro e pesquisa. Algumas operações de exclusão e pesquisa dinâmica recebem dados em JSON.

### 2. Organização por módulos

As operações relacionadas às entidades foram distribuídas em módulos Python, como `alunos`, `professores`, `cursos`, `secretaria`, `matriculas` e `faltas`.

Essa organização permite concentrar as funções de cada domínio em arquivos específicos, reduzindo a necessidade de implementar todas as operações diretamente nas rotas.

### 3. Integração com MySQL

A persistência dos dados é realizada por meio do MySQL Connector/Python. A aplicação configura os parâmetros de conexão e utiliza uma função dedicada para estabelecer a comunicação com o banco de dados `cursosbd`.

As operações de consulta, inserção, atualização e exclusão utilizam essa conexão para manipular os registros escolares.

### 4. Interface e formulários

As páginas são renderizadas pelo Flask utilizando templates HTML organizados por módulos. Os formulários permitem inserir e editar informações, enquanto as páginas de pesquisa apresentam os resultados retornados pelo back-end.

O sistema também utiliza JavaScript para interações dinâmicas, incluindo requisições que retornam sugestões de nomes em formato JSON.

### 5. Pesquisa dinâmica

Foram implementadas funcionalidades de pesquisa com campos opcionais e sugestões de valores próximos ao texto digitado.

Esses recursos auxiliam na localização de pessoas, professores, cursos e turmas, além de permitir o preenchimento de campos com base em registros existentes no banco de dados.

### 6. Estilização com Tailwind CSS

A interface utiliza Tailwind CSS para definir o estilo das páginas. O arquivo `tailwind.config.js` configura os diretórios analisados pelo Tailwind e personaliza a tipografia e a paleta de cores do projeto.

O CSS final é gerado a partir do arquivo de entrada `cursos-main/static/style.css`, com saída em `cursos-main/static/output.css`.

## 📋 Requisitos

Antes de executar o projeto, instale:

- Python 3.
- MySQL Server.
- Node.js e npm.
- Git.

## 🚀 Instalação e execução

### 1. Clonar o repositório

```bash
git clone https://github.com/JoaoVitorBerger/projetoEscola.git
cd projetoEscola
```

### 2. Configurar o ambiente Python

Entre na pasta da aplicação:

```bash
cd cursos-main
```

Crie e ative um ambiente virtual:

```bash
python -m venv .venv
```

No Windows, execute:

```bash
.venv\Scripts\activate
```

Instale as dependências Python:

```bash
pip install Flask mysql-connector-python
```

### 3. Configurar o banco de dados

Crie o banco de dados MySQL com o nome `cursosbd`.

No arquivo `app.py`, revise as configurações de conexão para corresponder ao ambiente local:

```python
db_config = {
    'host': 'localhost',
    'user': 'root',
    'passwd': '',
    'database': 'cursosbd'
}
```

Configure as credenciais de acordo com a instalação do MySQL e disponibilize as tabelas necessárias para o funcionamento dos módulos.

### 4. Instalar as dependências do Tailwind CSS

Volte para a raiz do repositório:

```bash
cd ..
npm install
```

Gere o CSS e mantenha o processo observando alterações nos arquivos:

```bash
npx tailwindcss -i cursos-main/static/style.css -o cursos-main/static/output.css --watch
```

Mantenha esse terminal aberto durante o desenvolvimento.

### 5. Iniciar a aplicação

Em outro terminal, entre na pasta `cursos-main`, ative o ambiente virtual e execute:

```bash
python app.py
```

A aplicação inicia o servidor Flask em modo de depuração. Acesse o endereço local indicado pelo terminal, normalmente `http://127.0.0.1:5000`.

## 📁 Estrutura do projeto

```text
projetoEscola/
├── cursos-main/
│   ├── app.py
│   ├── models/
│   │   ├── alunos.py
│   │   ├── cursos.py
│   │   ├── faltas.py
│   │   ├── inscricoes.py
│   │   ├── matriculas.py
│   │   ├── pessoa.py
│   │   ├── planosAula.py
│   │   ├── professores.py
│   │   ├── secretaria.py
│   │   ├── turmas.py
│   │   └── turmas_professores.py
│   ├── static/
│   │   ├── style.css
│   │   └── output.css
│   └── templates/
├── package.json
├── package-lock.json
└── tailwind.config.js
```

*Estrutura resumida dos principais componentes da aplicação.*

## 🎯 Objetivo do projeto

O projeto foi desenvolvido para praticar a construção de aplicações web com Python e Flask, integração com bancos de dados relacionais, organização do código em módulos, processamento de formulários e desenvolvimento de interfaces com HTML, JavaScript e Tailwind CSS.
