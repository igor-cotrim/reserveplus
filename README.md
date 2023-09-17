# Reservas

Sistemas de Reservas de ambientes

## Pré-requisitos

* Node.js v16 ou superior
* Docker
* Npm
* Yarn
* Outras dependências do projeto

## Instalação

1. Clone o repositório do projeto:
```bash
  git clone https://github.com/igor-cotrim/reservas.git
```

2. Instale as dependências do Front-end (client):
```bash
  cd nome-do-projeto
  cd client
  yarn 
  ou 
  npm install
```

3. Crie o arquivo .next com o comando:
```bash
  yarn build
  ou
  npm run build
```

3. Instale as dependências do Back-end (server):
```bash
  cd nome-do-projeto
  cd server
  yarn 
  ou 
  npm install
```

## Configuração

1. Na raiz do projeto crie o arquivo .env e copie o conteudo do .env.example:
```bash
  touch .env
```

2. Entre no client e crie o arquivo .env.local e copie o conteudo do .env.example:
```bash
  cd client
  touch .env.local
```

3. Entre no server e crie o arquivo .env e copie o conteudo do .env.example:
```bash
  cd server
  touch .env
```

</br>
<b>OBS: Lembre sempre de mudar onde está tobemodified para suas credencias</b>

## Iniciar

1. Para mudar o ambiente mude no arquivo .env na raiz do projeto o ENVIRONMENT

```bash
  ENVIRONMENT=development --> Para desenvolvimento
  ENVIRONMENT=production --> Para produção
```

2. Apos todos os envs configurados rode o comando para buildar as images
```bash
  docker-compose build
```

3. Apos buildar com sucesse rode o comando para rodar os containers
```bash
  docker-compose up
```

</br>
<b>OBS: Pode acontecer de demorar um pouco de subir o container do Strapi (Server), aguarde um pouco.</b>

## Primeiro acesso Strapi

1. Crie sua conta ADM no Strapi na rota
```bash
  http://0.0.0.0:1337/admin
```

2. Rode o comando a seguir para popular o banco de dados com algumas informacoes como um usuario Admin, semestres 2023.1 e 2023.2. Obs: Altere o DATABASE_NAME e DATABASE_USERNAME por suas credencias, mas mesmas do .env da raiz.
```bash
  docker exec -i serverDB psql -U <DATABASE_NAME> -d <DATABASE_USERNAME> < populate.sql
```

3. No Strapi, acesse Setting > Roles

4. No Authenticated, em permissions: 
- Ambience > Select All
- Reservation > Select All
- Semester > Select All
- Users-permissions > USER > Select All

5. No Public, em permissions: 
- Ambience > findOne e find
- Reservation > findOne e find
- Semester > findOne e find
- Users-permissions > USER > findOne, find e me
