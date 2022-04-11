---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Store API
---

# Introdução

Bem-vindo(a) à Store API!

Esta API foi criada com o intuito de aplicar os conhecimentos adquiridos à respeito de Spring Framework e construção de APIs. Sendo assim, as tecnologias utilizadas foram Spring Data para a manipulação de dados, Spring Security e JWT para autenticação e autorização, Spring Boot para ferramentas utilizadas durante o desenvolvimento e Gradle para controle de dependências. O banco de dados utilizado foi o h2 por questões de praticidade.

Os endpoints são \clientes, \pedidos e \produtos, juntamente com \auth para autenticação, que é realizada através de e-mail único de usuário e sua senha. Todos endpoints possuem os métodos do CRUD, portanto é possível criar, listar todos, listar específicos, atualizar e deletar recursos. A autorização é feita por token Bearer, e é necessária para acessar os recursos.

# Autenticação

> Para autenticação, utilize o seguinte código:

```ruby
require 'httparty'

response = HTTParty.post("http://store.com/auth", 
  body: { email: "user@example.com", senha: "senha" })

```

```python

import requests

response = requests.post('http://store.com/auth', 
  json = {"email": "user@example.com", "senha":"senha"})

```

```shell
curl -d '{"email":"user@example.com","senha":"senha"}' \
-H 'Content-Type:application/json' -X POST http://store.com/auth 
```

```javascript
const inputBody = '{
  "email": "user@example.com",
  "senha": "senha"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://store.com/auth',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

Para a autenticação, deve ser realizada uma requisição POST com o envio de um
JSON com os campos <code>email</code> e <code>senha</code>. 
Você então receberá um token Bearer que deverá ser utilizado em todas as outras requisições.

<code>{
    "email":"",
    "senha":""
    }
</code>

# Autorização

> Para autorização, utilize o seguinte código:

```ruby
require 'httparty'

response = HTTParty.metodo("url com endpoint desejado", 
  body: { JSON }, headers: {"Authorization: Bearer token" => 'token'}))

```

```python
import requests

headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer token'
}

response = requests.metodo('url com endpoint desejado', headers = headers, json = json)
```

```shell
curl "url com endpoint desejado" \
  -H "Authorization: Bearer token"
```

```javascript

const headers = {
  'Authorization':'Bearer token'
};

fetch('url com endpoint desejado',
{
  method: 'método desejado',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

> Você deve substituir `token` pelo seu token de autorização. Assim como o 
método e a URL do endpoint desejado.

A store API utiliza JWT token para autenticação e autorização. 

Você deve incluir o token no header das requisições:

`Authorization: Bearer token`

<aside class="notice">
Você deve substituir <code>token</code> pelo token fornecido ao realizar a autenticação.
</aside>

# Clientes

## Criar um cliente

```ruby
require 'httparty'

response = HTTParty.post("http://store.com/clientes", body: { JSON }, 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer token'
}

response = requests.post('http://store.com/clientes', headers = headers, json = json)
```

```shell
curl -X POST -d '{JSON}' \
-H "Content-Type:application/json" -H "Authorization: Bearer token" \
http://store.com/clientes
```

```javascript
const inputBody = JSON
const headers = {
  'Authorization':'Bearer token',
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://store.com/clientes',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna um JSON:

```json
{
  "id":"",
  "nome":"",
  "sobrenome":""
}
```

Esse endpoint cria um novo cliente. 


### JSON necessário

<code>
  {
    "nome":"",
    "sobrenome":"",
    "genero":"",
    "endereco":"",
    "cidade":"",
    "estado":"",
    "cep":"",
    "email":"",
    "senha":"",
    "cartaoCredito":""
  }
</code>

### HTTP Request

`POST http://store.com/clientes`


## Listar todos os clientes

```ruby
require 'httparty'

response = HTTParty.get("http://store.com/clientes", 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Authorization': 'Bearer token'
}

response = requests.get('http://store.com/clientes', headers = headers)
```

```shell
curl -X GET \
-H "Authorization: Bearer token" \
http://store.com/clientes
```

```javascript
const headers = {
  'Authorization':'Bearer token',
};

fetch('https://store.com/clientes',
{
  method: 'GET',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna um JSON:

```json
[
  {
  "id":"1",
  "nome":"",
  "sobrenome":""
  },
  {
  "id":"2",
  "nome":"",
  "sobrenome":""
  }
]
```

Esse endpoint retorna todos os clientes.

### HTTP Request

`GET http://store.com/clientes`


## Lista cliente específico

```ruby
require 'httparty'

response = HTTParty.get("http://store.com/clientes/ID", 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Authorization': 'Bearer token'
}

response = requests.post('http://store.com/clientes/ID', headers = headers)
```

```shell
curl -X POST \
-H "Authorization: Bearer token" \
http://store.com/clientes/ID
```

```javascript
const headers = {
  'Accept':'application/json'
};

fetch('https://store.com/clientes/ID',
{
  method: 'GET',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna o JSON:

```json
{
  "id":"",
  "nome":"",
  "sobrenome":""
}
```

Esse endpoint retorna um cliente específico através do seu ID.

### HTTP Request

`GET http://store.com/clientes/<ID>`

### URL Parameters

Parâmetro | Descrição
--------- | -----------
ID | O ID do cliente que deseja como retorno.

## Atualiza cliente específico

```ruby
require 'httparty'

response = HTTParty.put("http://store.com/clientes/ID", body: { JSON }, 
  headers: {"Authorization: Bearer token" => 'token'})  
```

```python
import requests

headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer token'
}

response = requests.put('http://store.com/clientes/ID', headers = headers, json = json)
```

```shell
curl -X PUT -d '{JSON}' \
-H "Content-Type:application/json" -H "Authorization: Bearer token" \
http://store.com/clientes/ID
```

```javascript
const inputBody = JSON
const headers = {
  'Authorization':'Bearer token',
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://store.com/clientes/ID',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna o JSON:

```json
{
  "id":"",
  "nome":"",
  "sobrenome":""
}
```

Esse endpoint atualiza um cliente específico através do seu ID.

### Necessário JSON

<code>
  {
    "nome":"",
    "sobrenome":"",
    "genero":"",
    "endereco":"",
    "cidade":"",
    "estado":"",
    "cep":"",
    "email":"",
    "senha":"",
    "cartaoCredito":""
  }
</code>

### HTTP Request

`PUT http://store.com/clientes/<ID>`

### URL Parameters

Parâmetro | Descrição
--------- | -----------
ID | O ID do cliente que deseja atualizar.

## Deletar cliente específico

```ruby
require 'httparty'

response = HTTParty.delete("http://store.com/clientes", 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Authorization': 'Bearer token'
}

response = requests.post('http://store.com/clientes/ID', headers = headers)
```

```shell
curl -X DELETE \
-H "Authorization: Bearer token" \
http://store.com/clientes/ID
```

```javascript
const headers = {
  'Accept':'application/json'
};

fetch('https://store.com/clientes/ID',
{
  method: 'DELETE',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna o JSON:

```json
{
  "id":"",
  "nome":"",
  "sobrenome":""
}
```

Esse endpoint deleta um cliente específico através do seu ID.

### HTTP Request

`DELETE http://store.com/clientes/<ID>`

### URL Parameters

Parâmetro | Descrição
--------- | -----------
ID | ID do cliente a ser deletado.


# Pedidos

## Criar um pedido

```ruby
require 'httparty'

response = HTTParty.post("http://store.com/pedidos", body: { JSON }, 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer token'
}

response = requests.post('http://store.com/pedidos', headers = headers, json = json)
```

```shell
curl -X POST -d '{JSON}' \
-H "Content-Type:application/json" -H "Authorization: Bearer token" \
http://store.com/pedidos
```

```javascript
const inputBody = JSON
const headers = {
  'Authorization':'Bearer token',
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://store.com/pedidos',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna um JSON:

```json
{
  "id":"",
  "cliente_id":"",
  "preco":""
}
```

Esse endpoint cria um novo pedido. 


### JSON necessário

<code>
  {
    "cliente_id":"",
    "itens":[
      {
        "produto_id":"",
        "quantidade":""
      },
      {
        "produto_id":"",
        "quantidade":""
      }
    ]
  }
</code>

### HTTP Request

`POST http://store.com/pedidos`


## Listar todos os pedidos

```ruby
require 'httparty'

response = HTTParty.get("http://store.com/pedidos", 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Authorization': 'Bearer token'
}

response = requests.get('http://store.com/pedidos', headers = headers)
```

```shell
curl -X GET \
-H "Authorization: Bearer token" \
http://store.com/pedidos
```

```javascript
const headers = {
  'Authorization':'Bearer token',
};

fetch('https://store.com/pedidos',
{
  method: 'GET',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna um JSON:

```json
[
  {
    "id":"",
    "cliente_id":"",
    "preco":""
  },
  {
    "id":"",
    "cliente_id":"",
    "preco":""
  }
]
```

Esse endpoint retorna todos os pedidos.

### HTTP Request

`GET http://store.com/pedidos`


## Lista pedido específico

```ruby
require 'httparty'

response = HTTParty.get("http://store.com/pedidos/ID", 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Authorization': 'Bearer token'
}

response = requests.post('http://store.com/pedidos/ID', headers = headers)
```

```shell
curl -X POST \
-H "Authorization: Bearer token" \
http://store.com/pedidos/ID
```

```javascript
const headers = {
  'Accept':'application/json'
};

fetch('https://store.com/pedidos/ID',
{
  method: 'GET',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna o JSON:

```json
{
  "id":"",
  "cliente_id":"",
  "preco":""
}
```

Esse endpoint retorna um pedido específico através do seu ID.

### HTTP Request

`GET http://store.com/pedidos/<ID>`

### URL Parameters

Parâmetro | Descrição
--------- | -----------
ID | O ID do pedido que deseja como retorno.

## Atualiza pedido específico

```ruby
require 'httparty'

response = HTTParty.put("http://store.com/pedidos/ID", body: { JSON }, 
  headers: {"Authorization: Bearer token" => 'token'})  
```

```python
import requests

headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer token'
}

response = requests.put('http://store.com/pedidos/ID', headers = headers, json = json)
```

```shell
curl -X PUT -d '{JSON}' \
-H "Content-Type:application/json" -H "Authorization: Bearer token" \
http://store.com/pedidos/ID
```

```javascript
const inputBody = JSON
const headers = {
  'Authorization':'Bearer token',
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://store.com/pedidos/ID',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna o JSON:

```json
{
  "id":"",
  "cliente_id":"",
  "preco":""
}
```

Esse endpoint atualiza um pedido específico através do seu ID.

### Necessário JSON

<code>
  {
    "cliente_id":"",
    "itens":[
      {
        "produto_id":"",
        "quantidade":""
      },
      {
        "produto_id":"",
        "quantidade":""
      }
    ]
  }
</code>

### HTTP Request

`PUT http://store.com/pedidos/<ID>`

### URL Parameters

Parâmetro | Descrição
--------- | -----------
ID | O ID do pedido que deseja atualizar.

## Deletar pedido específico

```ruby
require 'httparty'

response = HTTParty.delete("http://store.com/pedidos", 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Authorization': 'Bearer token'
}

response = requests.post('http://store.com/pedidos/ID', headers = headers)
```

```shell
curl -X DELETE \
-H "Authorization: Bearer token" \
http://store.com/pedidos/ID
```

```javascript
const headers = {
  'Accept':'application/json'
};

fetch('https://store.com/pedidos/ID',
{
  method: 'DELETE',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna o JSON:

```json
{
  "id":"",
  "cliente_id":"",
  "preco":""
}
```

Esse endpoint deleta um pedido específico através do seu ID.

### HTTP Request

`DELETE http://store.com/pedido/<ID>`

### URL Parameters

Parâmetro | Descrição
--------- | -----------
ID | ID do pedido a ser deletado.


# Produtos

## Criar um produto

```ruby
require 'httparty'

response = HTTParty.post("http://store.com/produtos", body: { JSON }, 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer token'
}

response = requests.post('http://store.com/produtos', headers = headers, json = json)
```

```shell
curl -X POST -d '{JSON}' \
-H "Content-Type:application/json" -H "Authorization: Bearer token" \
http://store.com/produtos
```

```javascript
const inputBody = JSON
const headers = {
  'Authorization':'Bearer token',
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://store.com/produtos',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna um JSON:

```json
{
  "id":"",
  "nome":"",
  "preco":""
}
```

Esse endpoint cria um novo produto. 


### JSON necessário

<code>
  {
    "nome":"",
    "preco":"",
    "categoria":"",
    "quantidadeDisponivel":""
  }
</code>

### HTTP Request

`POST http://store.com/produtos`


## Listar todos os produtos

```ruby
require 'httparty'

response = HTTParty.get("http://store.com/produtos", 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Authorization': 'Bearer token'
}

response = requests.get('http://store.com/produtos', headers = headers)
```

```shell
curl -X GET \
-H "Authorization: Bearer token" \
http://store.com/produtos
```

```javascript
const headers = {
  'Authorization':'Bearer token',
};

fetch('https://store.com/produtos',
{
  method: 'GET',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna um JSON:

```json
[
  {
    "id":"",
    "nome":"",
    "preco":""
  },
  {
    "id":"",
    "nome":"",
    "preco":""
  }
]
```

Esse endpoint retorna todos os pedidos.

### HTTP Request

`GET http://store.com/produtos`


## Lista pedido específico

```ruby
require 'httparty'

response = HTTParty.get("http://store.com/produtos/ID", 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Authorization': 'Bearer token'
}

response = requests.post('http://store.com/produtos/ID', headers = headers)
```

```shell
curl -X POST \
-H "Authorization: Bearer token" \
http://store.com/produtos/ID
```

```javascript
const headers = {
  'Accept':'application/json'
};

fetch('https://store.com/produtos/ID',
{
  method: 'GET',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna o JSON:

```json
{
  "id":"",
  "nome":"",
  "preco":""
}
```

Esse endpoint retorna um produto específico através do seu ID.

### HTTP Request

`GET http://store.com/produtos/<ID>`

### URL Parameters

Parâmetro | Descrição
--------- | -----------
ID | O ID do produto que deseja como retorno.

## Atualiza pedido específico

```ruby
require 'httparty'

response = HTTParty.put("http://store.com/produtos/ID", body: { JSON }, 
  headers: {"Authorization: Bearer token" => 'token'})  
```

```python
import requests

headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer token'
}

response = requests.put('http://store.com/produtos/ID', headers = headers, json = json)
```

```shell
curl -X PUT -d '{JSON}' \
-H "Content-Type:application/json" -H "Authorization: Bearer token" \
http://store.com/produtos/ID
```

```javascript
const inputBody = JSON
const headers = {
  'Authorization':'Bearer token',
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://store.com/produtos/ID',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna o JSON:

```json
{
  "id":"",
  "nome":"",
  "preco":""
}
```

Esse endpoint atualiza um produto específico através do seu ID.

### Necessário JSON

<code>
  {
    "nome":"",
    "preco":"",
    "categoria":"",
    "quantidadeDisponivel":""
  }
</code>

### HTTP Request

`PUT http://store.com/produos/<ID>`

### URL Parameters

Parâmetro | Descrição
--------- | -----------
ID | O ID do produto que deseja atualizar.

## Deletar produto específico

```ruby
require 'httparty'

response = HTTParty.delete("http://store.com/produtos", 
  headers: {"Authorization: Bearer token" => 'token'})
```

```python
import requests

headers = {
  'Authorization': 'Bearer token'
}

response = requests.post('http://store.com/produtos/ID', headers = headers)
```

```shell
curl -X DELETE \
-H "Authorization: Bearer token" \
http://store.com/produtos/ID
```

```javascript
const headers = {
  'Accept':'application/json'
};

fetch('https://store.com/produtos/ID',
{
  method: 'DELETE',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

> O comando acima retorna o JSON:

```json
{
  "id":"",
  "nome":"",
  "preco":""
}
```

Esse endpoint deleta um produto específico através do seu ID.

### HTTP Request

`DELETE http://store.com/produtos/<ID>`

### URL Parameters

Parâmetro | Descrição
--------- | -----------
ID | ID do produto a ser deletado.