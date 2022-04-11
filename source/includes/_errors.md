# Erros

A store API utiliza os seguintes códigos de erro:


Código | Significado
---------- | -------
400 | Bad Request -- Requisição inválida.
401 | Unauthorized -- O token não foi aceito.
403 | Forbidden -- O recurso não é autorizado para o token utilizado.
404 | Not Found -- O recurso requisitado não foi encontrado.
405 | Method Not Allowed -- Método não permitido ao recurso requisitado.
500 | Internal Server Error -- Problemas com o servidor. Tentar novamente mais tarde.
