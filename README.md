# API de Biblioteca

APi para cadastramento de usuários e livros, fazendo reservas dos livros.

Todas as rotas preican do token.

URL base : https://json-server-atv1.herokuapp.com

## USUÁRIO

## Cadastramento de usuário

### caminho POST https://json-server-atv1.herokuapp.com/signup

{
	"name": "tesste1",
	"email": "aca@a.com",
	"age": 8,
	"password": "123456"
}

sem nenhum erro aparecera

{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFjYUBhLmNvbSIsImlhdCI6MTY2MDM1MjExMSwiZXhwIjoxNjYwMzU1NzExLCJzdWIiOiI0In0.qnOjtS0sAdBcv0WQw1bEUyT1fG64QcZrExcfy2hFQRE",
	"user": {
		"email": "aca@a.com",
		"name": "tesste1",
		"age": 8,
		"id": 4
	}
}

Possiveis erros 
"Email already exists"

## Login
### Caminho POST https://json-server-atv1.herokuapp.com/login

{
	"email": "a@a.com",
	"password": "123456"
}

sem nenhum erro aparecera

{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFAYS5jb20iLCJpYXQiOjE2NjAzNTI0MDMsImV4cCI6MTY2MDM1NjAwMywic3ViIjoiMiJ9.lvc5BDl6_-zjCHMO5JGRI51GSal4jLkivyu1gQ542GM",
	"user": {
		"email": "a@a.com",
		"id": 2
	}
}

Possiveis erros 
"Cannot find user"


## Reservas do usuário GET https://json-server-atv1.herokuapp.com/users/2?_embed=books.reservation=true

verifica livros que o usuário reservou no sistema

}
	"email": "a@a.com",
	"password": "$2a$10$g88oDRUCYFxOLCrO.NyK0umTY34DXblPSIlDcPAMU.uMJLTHrCKq.",
	"id": 2,
	"books.reservation=true": []
}

## LIVROS
## Caminho GET https://json-server-atv1.herokuapp.com/books

Todos os livros

[
	{
		"name": "Cidade dos dragões",
		"Paginas": 467,
		"autohr": "autor",
		"reservation": true,
		"userId": 2,
		"id": 1
	},
	{
		"name": "Narnia",
		"Paginas": 467,
		"autohr": "autor",
		"reservation": false,
		"userId": 2,
		"id": 2
	}
]

## Criando novo livro

## Caminho POST https://json-server-atv1.herokuapp.com/books

userID - é o usuário logado.

{
	"name": "Narni2a",
	"Paginas": 467,
	"autohr": "autor",
	"reservation": false,
	"userId": 2
}

Retorno

id - identificação do livro

{
	"name": "Narni2a",
	"Paginas": 467,
	"autohr": "autor",
	"reservation": false,
	"userId": 2,
	"id": 3
}

## livros reservados ou não

so mudar o query reservation para false se quiser pesquisar livros nao reservados e true para livros reservados.

## Caminho GET https://json-server-atv1.herokuapp.com/books?reservation=true

[
	{
		"name": "Cidade dos dragões",
		"Paginas": 467,
		"autohr": "autor",
		"reservation": true,
		"userId": 2,
		"id": 1
	},
	{
		"name": "Narni2a",
		"Paginas": 467,
		"autohr": "autor",
		"reservation": true,
		"userId": 2,
		"id": 3
	}
]

## Reserva/ retira a reserva
## Caminho PATCH https://json-server-atv1.herokuapp.com/books/3

/books/bookId 
informe seu userId na requisição

se quiser retirar a reserva so mudar o reservation para false

{
	"reservation": true,
	"userId": 2
}

Retorno 

{
	"name": "Narni2a",
	"Paginas": 467,
	"autohr": "autor",
	"reservation": true,
	"userId": 2,
	"id": 3
}

##Deletar um livro
##Caminho DELETE https://json-server-atv1.herokuapp.com/books/3

books/bookId


