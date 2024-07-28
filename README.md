# Módulo de Docker do curso FullCycle
## Anotações da Aula

### Comandos apresentados nas aulas

Remover uma imgem

`docker rmi nome_da_imagem`

Remover várias imagens

`docker rm $(docker ps -a -q) -f`

Executar uma imagem de modo iterativo usando o bash

`docker run -it thyagodias/nginx-com-vim:latest bash`

Buildar uma imagem

`docker build -t thyagodias/nginx-com-vim:latest .`

Para buildar com um dockerfile diferente do padrão

`docker build -t thyagodias/nginx:prod . -f Dockerfile.prod`

Acessar um container que está rodando

`docker attach ubuntu1`

Limpar as imagens

`docker rm $(docker ps -a -q) -f`


### Network

- Bridge - O mais comum
- Host - Para comunicação entre o host que está rodando o docker com um container
- Overlay - 
- MacVlan - 
- None - Sinaliza que o container vai rodar de forma isolada, sem fazer parte de uma rede

Criar rede
`docker network create --driver bridge minharede`

Visualizar informações sobre uma rede
`docker network inspect minharede`

Rodar o container em uma rede
`docker run -dit --name ubuntu1 --network minharede bash`
`docker run -dit --name ubuntu2 --network minharede bash`

Conectar um container em uma rede
`docker network connect minharede ubuntu3`

Container acessando maquina host
`ping http://host.docker.internal:8080`