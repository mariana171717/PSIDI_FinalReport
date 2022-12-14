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

Também foi implementado um método de recuperação de palavra-passe.

## Testes
### Testes no POSTMAN
Nesta secção estão presentes os testes feitos para a API, no POSTMAN: 

- Testes de autenticação:
    - POST/User - Criação de utilizador na Base de Dados
       - Corretamente: 
           - 200 OK - Email inserido com sucesso
             ```
              Tudo okay!
             ```
       - Incorretamente:  
           - 400 Bad Request - Email inserido incorretamente
             ```
              "err": "O email esta invalido!"
             ```
           - 406 Not Acceptable - Email inserido já existe
             ```
             "err": "O email já existe!"
             ````
- Testes Users:
   - GET/User - Devolve todos os utilizadores existentes na Base de Dados
      - Corretamente:
          - 200 OK - Exemplo: 

             ![image](https://user-images.githubusercontent.com/119684676/207619197-2ef79a56-a721-4a21-8c24-2ceab0261202.png)

  - GET/User/id - Devolve o utilizador com o id especificado
      -  Corretamente:
           ```
           - 200 OK
           ```
      - Incorretamente:
           ```
           - 404 - Not Found 
           ```
  - PUT/User/ - Editar utilizador
      - Corretamente:
          ```
          - 200 ok
          ```
       - Caso id do user nao exista:
          ```
          - O utilizador nao existe.
          ```
       - Caso introduza email já existente: 
          ```
          - O email já está registado. - 406 - Not Acceptable
          ```
  - DELETE/User/:id - Apagar utilizador
      - Corretamente:
          ```
          - 200 ok - Utilizador é apagado da Base de Dados
          ```
      - Cado id nao exista:
          ```
          - 406 Not acceptable - O utilizador nao existe, logo nao pode apagar!.
          ```
  - POST/recoverpassword - Recuperar palavra-passe do utilizador
      - Corretamente:

  

## Código
O código está dividido em várias pastas. 
 - **routes/routes.js:** Encontra-se todas as rotas criadas, utilizando os métodos **GET, POST,PUT,DELETE.**
 - **database/connection.js:** Encontra-se os dados necessários para a conexão com a base de dados criada. 
 -

## Utilizadores
A API pode ter dois tipos de utilizadores. Os administradores e o utilizador normal. 
Este papel é definido na tabela **users**, através do atributo **role**.
  
   - Role=1, trata-se de um Admin
   - Role=0, trata-se de um utilizador comum.


