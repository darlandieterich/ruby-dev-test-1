# ruby-dev-test-1

Desenvolver a camada de modelos de um sistema de arquivos persistido em um banco de dados SQL onde seja possível criar diretórios e arquivos. Os diretórios poderão conter sub-diretórios e arquivos. O conteúdo dos arquivos podem estar ser persistidos como blob, S3 ou mesmo em disco.

A soluçãos deverá ser escrita majoritariamente em Ruby com framework Ruby on Rails.

Realizar um fork deste repositório.

===============

## Implementação

Para implementar o proposto, usei o docker para virtualizar o banco de dados para persistência com a aplicação, e acabei adotando a API do Rails. Tenho efetuado basicamente o principio de upload de arquivo para armazenar em banco de dados. Tive o foco na criação de diretórios e arquivo de forma que possa montar a estrura de diretórios conforme o caminho informado, e também é possível visualizar a árvore estrutural de forma recursiva percorrendo os objetos.

1. Primeiramente iniciar o banco de dados com o comando `docker-compose start`.

2. Em seguinda iniciar a API com o comando `rails s`.

3. Basicamente para enviar um arquivo deverá requisitar a url [POST] `http://localhost:3000/api/v1/manage/upload`. Setar os campos em formato (multipart/form-data) `file` (aqui define o arquivo) e `path` (aqui define o caminho onde irá armazenar o arquivo).

4. Para visualizar a estrutura de arquivo, deverá requisitar a url [GET] `http://localhost:3000/api/v1/directory/tree`. Setar o parâmetro `name` definindo um nome de diretório.
