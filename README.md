# PSIDI
# API de gestão de planos de musica
Esta Api foi desenvolvida 




## Base de dados
A base de dados utilizada neste projeto é a HeidiSQL.

Foi criada uma base de dados, com o nome de **apiusers**. 

Foi criada a tabela 'Users' para armazenar todos os utilizadores da aplicacao. Esta tabela contem os seuintes campos: id, name, email, password, role. Neste caso o role permite a distincao entre um funcionario e um administrador.
**Nota**: O email tem de ser obrigatoriamente unico. (nao tem repetidos.)

Foi criada uma table **passwordtokens**, onde será armazenado o token de cada utilizador.

Foi criada uma table **plans** com os campos: name, id, NumberMinutes, NumberUsers, MusicCollections, MusicSuggestions, MontlhyFee, AnualFee, Active. Estes campos representam todos os atributos que um plano pode ter. 


## Encriptação de palavra passe
Para a encriptação da palavra passe foi utilizado o método bcrypt. Para a instalação deste método: **npm install bcrypt --save**

Na base de dados, a palavra passe nao será visível, irá aparecer no seguinte formato:

![image](https://user-images.githubusercontent.com/119684676/207591221-3eb359e4-cac6-4b37-ba06-bb1a3d7bc15f.png)

Também foi implementado um método de recuperação de palavra-passe.
Para que isto fosse possível, houve a necessidade da criação de uma nova tabela na base de dados: **passwordtokens**, onde será guardado o token de cada um dos utilizadores que pretenda recuperar a palavra-passe. 
## Testes
### Testes no POSTMAN
Nesta secção estão presentes os testes feitos para a API, no POSTMAN: 

- Testes de autenticação:
    - Foi testado a autenticação, já com as permissões de Admin ou User normal
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
          ```
          Devolve o token - 200 - OK
          ```
      - Caso o email nao existe :
          ```
          O email nao existe! - 406 - Not Acceptable
          ```
  - POST/changepassword - Alterar palavra-passe do utilizador
      - Corretamente:
          ```
          Senha alterada - 200 - OK
          ```
      - Se inserirmos o token errado OU inserirmos novamente o token :
          ```
          Token inválido! - 406 - Not Acceptable
          ```
- Testes Login:
  - POST/login - Efetuar o login
    - Corretamente:
          ```
          Devolve o token correspondente
          ```
    - Caso a senha esteja correta:
          ```
          406 - Not Acceptable - Senha incorreta!
          ```

- Testes Plans:
  - POST/plan - Criar um plano
    - Corretamente:
          ```
          200 - Tudo Okay!
          ```
    - Caso o plano senha criado sem o campo "name":
          ```
          406 - Not Acceptable - Senha incorreta!


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

Para garantir que só os admins alteram/apagam/inserem dados na API, foi criado o folder: **Middleware**

## Login
Para o Login, foi necessário instalar a seguinte biblioteca: **npm install --save jsonwebtoken**

## Run the project
First, to run the project insert: npm install
Second, to run the server enter: nodemon index.js, inside que Manage_api folder
The port where the server will run is: 8686

## Planos
Ao criar um novo plano, existe primeiramente a verificação se nao existe um plano com aquele nome. Planos diferentes nao podem ter o mesmo nome. 


