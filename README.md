## PROJETO FUSION

### TRABALHANDO COM CLASS BASED VIEWS NO PYCHARM / DJANGO / POSTGRESQL

Projeto simples de uma página html feita em Django/class-based-views
utilizando o banco de dados PostgresSQL.

### Cria um diretório com o nome do projeto (fusion) num ambiente virtual

### Instala o django e outras aplicações (bibliotecas) que pecisa para o projeto:

		 - django
		 - psycopg2-binary (biblioteca para Posgresql)
		 - gunicorn (para rodar o projeto no heroku)
		 - dj-static (para os arquivos estáticos)
		 - django-stdimage(para trabalhar com imagens)
		 
		 	"pip install django psycopg2-binary gunicorn dj-static django-stdimage"

### Cria o arquivo requirements.txt:

	"pip freeze > requirements.txt"

### Cria projeto base com o mesmo nome do projeto com espaço ponto no final para que seja criado dentro do projeto:

	"django-admin startproject fusion ."
	
### Cria uma aplicação core:

	"django-admin startapp core"
	
### Cria os diretórios "templates" e "static" dentro da aplicação core
	
### Configura  o básico no settings

### Configura o porgresql no settings:

	DATABASES = {
	    'default': {
		'ENGINE': 'django.db.backends.postgresql',
		'NAME': 'fusion',
		'USER': '(nome do usuario)',
		'PASSWORD': '*******',
		'HOST': 'localhost',
		'PORT': '5432'
	    }
	}

### Configura a urls.py no projeto base "fusion"

	from django.urls import path, include
	from django.conf.urls.static import static
	from django.conf import settings

	urlpatterns = [
	    path('admin/', admin.site.urls),
	    path('', include('core.urls')),
	] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)


### Cria arquivo "urls.py" na aplicação "core" e configura depois de criar as rotas:

	from django .url import path

	urlspatterns = [

	]
	
### No pgadmin cria um banco de dados no POSTGRESQL, com o nome do projeto.

### Abre arquivo "views.py" da aplicação "core":

### importa do pacote django views generic o TemplateView e Cria uma classe "IndexView" que herda de "TemplateWiew" informando o nome do template:

		from django.views.generic import TemplateView
		
		class IndexView(TemplateView):
    			template_name = 'index.html'
			
	
### Na "urls.py" da aplicação "core" e configura as rotas:

	Importa o "path" e o "IndexView" do arquivo "views.py" da aplicação "core"
	
		from django.url import path
		from .views import IndexView

	Define uma rota para raiz do projeto:
	
	urlspatterns = [
		path('', IndexView.as_view(), name='index'),
	]

Commit: Adicionando configurações parte2 (configurando views.py e urls.py) no arquivo README

========================================================================

### No diretório "Templates da aplicação "Core"
 	Criar um arquivo "html" com o nome "index.html" deixando nesse formato:
 	
		<html lang="en">
		<head>
		    <meta charset="UTF-8">
		    <title>Title</title>
		</head>
		<body>
		    <h1>Index</h1>
		</body>
		</html>

Commit: Adicionando configurações parte 3 (Criando arquivo index.html e modificando arquivo README)

=================================================================================