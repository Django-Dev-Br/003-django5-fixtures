# 003 Django 5 -  Fixtures  - Backups e Restore de Banco de Dados

### O que são Fixtures no Django?

Fixtures são arquivos que contêm dados em formato JSON, XML, ou YAML que podem ser usados para carregar ou restaurar dados em um banco de dados Django. 

[Configura a documentação do Django sobre esse tópico](https://docs.djangoproject.com/en/5.1/topics/db/fixtures/#:~:text=A%20fixture%20is%20a%20collection,multiple%20directories%2C%20in%20multiple%20applications)

## COMO RODAR ESSE PROJETO EM SEU COMPUTADOR:

### Requisitos

- [GIT](https://git-scm.com/downloads/win)
- **[Python 3.12 com PIP e venv](https://www.python.org/)**
- **o Django 5 requer Python 3.10 ou superior.**
- **No [repositório 001](https://github.com/Django-Dev-Br/001-django5-basic-project) há explicações sobre PIP e venv**

  [Baixar Python 3.12](https://www.python.org/downloads/release/python-3122/)

  Confira o vídeo para saber como trabalhar com múltiplas versões do Python e com venv (ambiente virtual):
   [![Watch the video](https://img.youtube.com/vi/cxsaUE5JzDk/0.jpg)](https://youtu.be/cxsaUE5JzDk)


### 10 passos simples para executar

1. **Clone o repositório**:
    ```bash
    git clone https://github.com/Django-Dev-Br/003-django5-fixtures.git
    ```

2. **Crie  um ambiente virtual no diretório root**:

   **Windows**
    ```bash
     python -m venv myvenv 
    ```
      **Linux**
     ```bash
     python3 -m venv myvenv  
    ```

3. **Ative o ambiente virtual criado**:

   **Windows**
    ```bash
    myvenv\Scripts\activate  
    ```

     **Linux**
    ```bash
    source myvenv/bin/activate  
    ```
    
4. **Acesse a pasta do repositório**:
   
    ```bash
    cd 003-django5-fixtures
    ```
    
6. **Instale o Django**:

   Fazer a instalação após a ativação da virtual env fará com que a instalação seja feita nessa pasta ao invés do computador. Isso significa que o pacote Django não estará disponivel para todos os usuários do computador, mas apenas para o contexto no qual essa venv esteja ativada. Veremos sua ativação logo abaixo.

    **Instalação manualmente via gerenciador de dependências PIP**
    ```bash
    pip install django
    ```
    - use, preferencialmente, a versão 5.1. Para tanto, execute o comando:

     ```bash
    pip install  "django>=5.1,<=5.2"
    ```
    ----- **OU** -----

    **Instalação via arquivo requirements**
    ```bash
    pip install -r requirements.txt
    ```
    O arquivo requirements.txt é um arquivo de texto que contém uma lista de pacotes a ser instalado em uma venv. É uma boa prática de programação do ecossistema Python.
   
    
7. **Execute as migrações do banco de dados**:
    ```bash
    python manage.py migrate
    ```

8. **Carregar o Fixture**:
    Se precisar restaurar os dados do superusuário a partir do fixture, use o seguinte comando:

    ```bash
    python manage.py loaddata superuser_fixture.json
    ```
    - Isso carregará os dados do superusuário armazenados no fixture `superuser_fixture.json`. O superuser é admin e a senha é root
   
9. **Execute o servidor de desenvolvimento**:
    ```bash
    python manage.py runserver
    ```
    - Após executar o servidor de desenvolvimento, você pode acessar o Django Admin no seguinte endereço:

[http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)

Faça login com as credenciais do superusuário carregadas pelo fixture. O superuser é admin e a senha é root

9. **Criar um Fixture com os dados do superusuário**:
    ```bash
    python manage.py dumpdata auth.user --indent 4 > superuser_fixture.json
    ```

    Este comando salva os dados do superusuário em um arquivo JSON chamado `superuser_fixture.json`. O arquivo será gerado na raiz do projeto.


### Estrutura de Diretórios do Projeto

```
003-django5-fixture-example/
├── .gitignore             # Arquivo que especifica quais arquivos e diretórios o Git deve ignorar (não incluir no versionamento)
├── superuser_fixture.json  # Fixture contendo cópias dos dados do superusuário extraídas do banco de dados db.sqlite3
├── db.sqlite3              # Banco de dados SQLite criado após as migrações
├── myproject/
│   ├── __init__.py         # Marca o diretório como um pacote Python
│   ├── asgi.py             # Configurações para o servidor ASGI (usado para aplicações assíncronas)
│   ├── settings.py         # Configurações do projeto (banco de dados, apps instalados, etc.)
│   ├── urls.py             # Mapeamento de requisições HTTP e redirecionamento para os templates HTML
│   └── wsgi.py             # Configurações para o servidor WSGI (usado para servir a aplicação)
└── manage.py               # CLI do Django, um script de linha de comando para tarefas administrativas do Django
└── requirements.txt    # Lista de pacotes Python necessários para o projeto

```
### OBS: Observação sobre Fixtures no Django 5

Ao utilizar fixtures no Django 5, pode ocorrer um problema com caracteres especiais (como acentuações). Por exemplo a palavra "João" pode ficar assim: "Jo�o". Isto é, o Django pode gerar arquivos de fixture contendo caracteres incorretos ou codificados de forma errada. Isso impedirá o carregamento da fixture. Nesses casos, a mensagem de erro é algo assim: "UnicodeDecodeError: 'utf-8' codec can't decode byte 0xe3 in position 795: invalid continuation byte".

**Solução**: É recomendável inspecionar o arquivo de fixture gerado e verificar se há problemas com a codificação dos caracteres especiais. Caso encontre caracteres incorretos, faça a correção manual diretamente no arquivo

### OBS: Como Criar um Projeto Django

Se desejar criar seu próprio projeto Django, use o seguinte comando após criar e ativar a virtual env e instalar o django nela, conforme orientações acima:

```bash
django-admin startproject myproject
```

### Sobre Nosso Treinamento Prático-Profissional com projeto real para iniciantes e avançados em web DevOps Full-stack com Python, Django, Bootstrap e Linux.

[Django Developers Brasil - Aprenda programando enquanto programa aprendendo!](https://django.dev.br/)

Nosso treinamento oferece uma experiência prática de aprendizado de programação, adequada tanto para iniciantes quanto para desenvolvedores avançados. Você participará de um projeto real de desenvolvimento de software em um ambiente corporativo autêntico, onde pessoas com diferentes níveis de conhecimento irão colaborar, aprendendo umas com as outras.

**Junte-se a nós!** E desenvolva as habilidades necessárias para o mercado de trabalho, aprimorando tanto seus conhecimentos técnicos quanto suas soft skills em um ambiente colaborativo e realista.

