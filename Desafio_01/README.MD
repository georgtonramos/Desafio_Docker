# Desafio 01 - Mongo Db + Mongo Express

Criar um MongoDB e o Mongo Express usando o docker compose + Ajustes de limitação de CPU e Memoria + Ajustes de segurança

- Limitado o Uso de CPU a 50%
- Limitado o consumo de memoria em 1024 MB

**Volumes**

Um volume é definido com o nome mongodb. Este volume será utilizado para persistência dos dados do MongoDB.

**Networks**

Uma rede de nome mongodb_net é definida com o driver bridge. Esta rede será utilizada pelos serviços para se comunicarem entre si.

**Serviços**

Dois serviços são definidos: mongodb e mongo-express.

**Serviço: mongodb**

**'image'**: A imagem docker utilizada é a mongo:latest, que é a versão mais recente da imagem oficial do MongoDB.

**'container_name'**: O nome do container será mongo.

**'environment'**: Define duas variáveis de ambiente, MONGO_INITDB_ROOT_USERNAME e MONGO_INITDB_ROOT_PASSWORD, cujos valores devem ser definidos no ambiente onde este arquivo será executado.

**'volumes'**: Este serviço usa o volume mongodb, montando-o em /data/db, que é o local padrão onde o MongoDB armazena seus dados.
ports: O serviço será acessível na porta 27017, tanto dentro do container quanto no host.

**'networks'**: Este serviço utilizará a rede mongodb_net.

**'deploy'**: Os recursos de CPU e memória deste serviço estão limitados a 0.5 CPU e 1024M de memória.

**Serviço: mongo-express**

**'image'**: A imagem docker utilizada é a mongo-express:latest, que é a versão mais recente da imagem oficial do Mongo-Express, uma interface de administração web para o MongoDB.
    
**'container_name'**: O nome do container será mongo-express.
**'environment'**: Define três variáveis de ambiente. ME_CONFIG_MONGODB_SERVER é definido como mongodb, que é o nome do serviço MongoDB que foi definido acima. ME_CONFIG_MONGODB_ADMINUSERNAME e ME_CONFIG_MONGODB_ADMINPASSWORD são os mesmos definidos no serviço MongoDB.
    
**'ports'**: O serviço será acessível na porta 8081, tanto dentro do container quanto no host.

**'networks'**: Este serviço utilizará a rede mongodb_net.

**'deploy'**: Os recursos de CPU e memória deste serviço estão limitados a 0.5 CPU e 1024M de memória.

**Executando o Compose File**

Para rodar esse arquivo Docker Compose, primeiro você precisa definir as variáveis de ambiente MONGO_INITDB_ROOT_USERNAME e MONGO_INITDB_ROOT_PASSWORD. Depois, você pode executar o comando docker-compose up no mesmo diretório do arquivo.