# Cosmo Books

Sistema de cadastro de livros e consulta/cadastro de API's externas

## Installation

- **Necessário o docker engine ou desktop instalado em sua maquina**
  - [Instalação Docker engine - ubuntu](https://docs.docker.com/engine/install/ubuntu/)

Clonar o projeto em um diretório de sua preferência
```bash
Exemplo de diretório: projects

cd projects
git clone https://github.com/willdalp/cosmo-books.git
cd cosmo-books
```

Se você está rodando o Sail pela primeira vez, você pode precisar tornar o script do Sail executável
```bash
chmod +x ./vendor/bin/sail
```
Depois você pode iniciar o comando para subir os containers. Se você não tiver o Docker rodando, o Sail pedirá para iniciá-lo:
```bash
./vendor/bin/sail up
```

Copie o arquivo .env.example para .env e ajuste as configurações de acordo com o seu ambiente local:
```bash
cp .env.example .env
```
Instale as dependências
```bash
./vendor/bin/sail composer install
```

Gera a chave da aplicação
```bash
./vendor/bin/sail artisan key:generate
```

Execute as migrates para criar as tabelas no banco de dados (depois que configurado a .env)
```bash
./vendor/bin/sail artisan migrate
```
Rode o para o front com vue e inertia
```bash
npm run dev
```
Agora com os container rodando e o front, o projeto pode ser acessado em http://localhost.