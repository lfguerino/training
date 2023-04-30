# Training

Este é um projeto básico de servidor HTTP escrito em Node.js que implementa rotas simples. Ele utiliza o módulo nativo http e o módulo url para fazer o parsing das URLs. O servidor escuta na porta 3000 e implementa quatro rotas que estão definidas no arquivo routes.js. As rotas implementadas são: listar usuários, obter usuário por ID, criar usuário, atualizar usuário e excluir usuário.

## UserController
O arquivo UserController.js define as funções que implementam as rotas do servidor. Essas funções são responsáveis por manipular a lista de usuários que é mantida em memória no arquivo users.js na pasta mocks.

#### listUsers
A função listUsers retorna a lista de usuários ordenada pelo ID. A ordenação pode ser ascendente (padrão) ou descendente, dependendo do valor do parâmetro order na query string da URL.

#### getUserById
A função getUserById retorna um único usuário com base no ID passado como parâmetro na URL. Se o usuário não for encontrado, uma resposta de erro é enviada com código 400.

#### createUser
A função createUser cria um novo usuário com base nos dados enviados no corpo da requisição e o adiciona à lista de usuários. O ID do novo usuário é gerado automaticamente com base no último ID existente na lista.

#### updateUser
A função updateUser atualiza o nome de um usuário com base no ID passado como parâmetro na URL e no novo nome enviado no corpo da requisição. Se o usuário não for encontrado, uma resposta de erro é enviada com código 400.

#### deleteUser
A função deleteUser exclui um usuário com base no ID passado como parâmetro na URL. Se o usuário não for encontrado, uma resposta de erro é enviada com código 400.

---

## bodyParser
O bodyParser é um middleware utilizado para interpretar e parsear o corpo das requisições que chegam no servidor, no formato JSON. Este arquivo contém apenas uma função, bodyParser, que recebe dois parâmetros:

- **request**: representa o objeto de requisição enviado pelo cliente.
- **callback**: é uma função que será chamada assim que o corpo da requisição estiver disponível para ser parseado.

A função bodyParser é responsável por ler o corpo da requisição (que é passado em chunks) e armazenar em uma variável chamada body. Quando a leitura do corpo é finalizada, a variável body é parseada em JSON e armazenada no objeto request na propriedade body. Por fim, a função callback é chamada para que o fluxo de execução da requisição possa continuar.

Este middleware é utilizado no arquivo index.js em conjunto com as rotas da aplicação para parsear o corpo das requisições enviadas nos métodos POST, PUT e PATCH.
