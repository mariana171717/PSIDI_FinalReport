# PSIDI
# API de gestão de planos de musica
Esta Api foi desenvolvida 




## Base de dados
A base de dados utilizada neste projeto é a HeidiSQL.

Foi criada uma base de dados, com o nome de 'apiusers', sendo criada uma tabela chamada 'users', onde serao armazenados todos os utilizadores da aplicacao.
A table users contem os campos: id, name, email, password, role.
Neste caso o role permite a distincao entre um funcionario e um administrador.


O email tem de ser obrigatoriamente unico. (nao tem repetidos.)


## Testes
### Testes no POSTMAN
- Testes de autenticação:
    - POST/User
       - 200 OK
         ```
          Tudo okay!
         ```
       - 400 Bad Request
         ```
          "err": "O email esta invalido!"
         ```

