# 003 Django 4 Fixture  - Backups e Restore de Banco de Dados

### O que são Fixtures no Django?

Fixtures são arquivos que contêm dados em formato JSON, XML, ou YAML que podem ser usados para carregar ou restaurar dados em um banco de dados Django. 

## COMO RODAR ESSE PROJETO EM SEU COMPUTADOR:

### Requisitos

- **Python 3.12**  
  [Baixar Python 3.12](https://www.python.org/downloads/release/python-3122/)

  Confira o vídeo para saber como trabalhar com múltiplas versões do Python e com venv (ambiente virtual): [Trabalhando com Múltiplas Versões do Python + venv](https://youtu.be/eetDeQrv0Rs?si=rAIDmLCgdeh7ouXa)

- **Virtualenv**

  Para instalar o pacote `virtualenv` no Python, utilize os seguintes comandos:

  - **Linux**:
    ```bash
    python3 -m pip install virtualenv
    ```

  - **Windows**:
    ```bash
    python -m pip install virtualenv
    ```

### Passos para Executar

1. **Clone o repositório**:
    ```bash
    git clone https://github.com/Django-Dev-Br/003-django-4-fixtures.git
    003-django-4-fixtures
    ```

2. **Crie um ambiente virtual**:
    ```bash
    python3 -m venv myvenv  # Linux
    python -m venv myvenv  # Windows
    ```

3. **Ative o ambiente virtual criado**:
    ```bash
    source myvenv/bin/activate  # Linux
    myvenv\Scripts\activate  # Windows
    ```

4. **Instale o Django**:
    ```bash
    pip install django==4.2.15
    ```

5. **Execute as migrações do banco de dados**:
    ```bash
    python manage.py migrate
    ```

6. **Crie um superusuário**:
    ```bash
    python manage.py createsuperuser
    ```

    Após criar o superusuário, vamos salvar esses dados como um fixture.

7. **Criar um Fixture com os dados do superusuário**:
    ```bash
    python manage.py dumpdata auth.user --indent 4 > superuser_fixture.json
    ```

    Este comando salva os dados do superusuário em um arquivo JSON chamado `superuser_fixture.json`. O arquivo será gerado na raiz do projeto.

8. **Carregar o Fixture**:
    Se precisar restaurar os dados do superusuário a partir do fixture, use o seguinte comando:

    ```bash
    python manage.py loaddata superuser_fixture.json
    ```

    Isso carregará os dados do superusuário armazenados no fixture `superuser_fixture.json`.

9. **Execute o servidor de desenvolvimento**:
    ```bash
    python manage.py runserver
    ```

### Acesse o Django Admin no seu navegador:

Após executar o servidor de desenvolvimento, você pode acessar o Django Admin no seguinte endereço:

[http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)

Faça login com as credenciais do superusuário carregadas pelo fixture.

### Estrutura de Diretórios do Projeto

```
003-django4-fixture-example/
├── superuser_fixture.json  # Fixture contendo cópias dos dados do superusuário extraídas do banco de daddos db.sqlite3
├── db.sqlite3              # Banco de dados SQLite criado após as migrações
├── myproject/
│   ├── __init__.py         # Marca o diretório como um pacote Python
│   ├── asgi.py             # Configurações para o servidor ASGI (usado para aplicações assíncronas)
│   ├── settings.py         # Configurações do projeto (banco de dados, apps instalados, etc.)
│   ├── urls.py             # Mapeamento de requisições HTTP e redirecionamento para os templates HTML
│   └── wsgi.py             # Configurações para o servidor WSGI (usado para servir a aplicação)
└── manage.py               # CLI do Django, um script de linha de comando para tarefas administrativas do Django
```

### Sobre Nosso Treinamento Prático-Profissional com projeto real para iniciantes e avançados em web DevOps Full-stack com Python, Django, Bootstrap e Linux.

[Django Developers Brasil - Aprenda programando enquanto programa aprendendo!](https://django.dev.br/)

Nosso treinamento oferece uma experiência prática de aprendizado de programação, adequada tanto para iniciantes quanto para desenvolvedores avançados. Você participará de um projeto real de desenvolvimento de software em um ambiente corporativo autêntico, onde pessoas com diferentes níveis de conhecimento irão colaborar, aprendendo umas com as outras.

**Junte-se a nós!** E desenvolva as habilidades necessárias para o mercado de trabalho, aprimorando tanto seus conhecimentos técnicos quanto suas soft skills em um ambiente colaborativo e realista.

