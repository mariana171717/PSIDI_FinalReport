# PSIDI
# API de gestão de planos de musica
Esta Api foi desenvolvida 




## Base de dados
A base de dados utilizada neste projeto é a HeidiSQL.

Foi criada uma base de dados, com o nome de **apiusers**, sendo criada uma tabela chamada 'users', onde serao armazenados todos os utilizadores da aplicacao.
A table users contem os campos: id, name, email, password, role.
Neste caso o role permite a distincao entre um funcionario e um administrador.

O email tem de ser obrigatoriamente unico. (nao tem repetidos.)

## Encriptação de palavra passe
Para a encriptação da palavra passe foi utilizado o método bcrypt. Para a instalação deste método: **npm install bcrypt --save**

Na base de dados, a palavra passe nao será visível, irá aparecer no seguinte formato:

![image](https://user-images.githubusercontent.com/119684676/207591221-3eb359e4-cac6-4b37-ba06-bb1a3d7bc15f.png)



## Testes
### Testes no POSTMAN
- Testes de autenticação:
    - POST/User
       - 200 OK - Email inserido com sucesso
         ```
          Tudo okay!
         ```
       - 400 Bad Request - Email inserido incorretamente
         ```
          "err": "O email esta invalido!"
         ```
       - 406 Not Acceptable - Email inserido já existe
         ```
         "err": "O email já existe!"
         ````
- Testes GetUsers:
  - GET/User - Devolve users existentes na Base de Dados
        ````
       - 200 OK - Devolve users existentes na Base de Dados
        ````

