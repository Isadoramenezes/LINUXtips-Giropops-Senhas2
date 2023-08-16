# Linuxtips Giropops Senhas

Esse repositório contém o código para o desafio 2 do Programa Intensivo de Kubernetes e Containers.

A lista de requisitos desse desafio é:

- [x] Criar um conta no Docker Hub, caso ainda não possua uma.
- [x] Criar uma conta no Github, caso ainda não possua uma.
- [x] Criar um Dockerfile para criar uma imagem de container para a nossa App
- [x] O nome da imagem deve ser SEU_USUARIO_NO_DOCKER_HUB/linuxtips-giropops-senhas:1.0
- [x] Fazer o push da imagem para o Docker Hub, essa imagem deve ser pública
- [x] Criar um repo no Github chamado LINUXtips-Giropops-Senhas, esse repo deve ser público
- [x] Fazer o push do cógido da App e o Dockerfile
- [x] Criar um container utilizando a imagem criada
- [x] O nome do container deve ser giropops-senhas
- [x] Você precisa deixar o container rodando
- [x] O Redis precisa ser um container

Dica: Preste atenção no uso de variável de ambiente, precisamos ter a variável REDIS_HOST no container. Use sua criatividade!


## Como validar esse desafio

1. Criar uma network para o container da aplicação se comunicar com o redis:

```bash
docker network create -d bridge strigus
```

2. Iniciar um container do Redis nessa rede:

```bash
docker run -d -p 6379:6379 --name myredis --network strigus redis
```

3. Executar um container com a imagem `isadora/linuxtips-giropops-senhas:1.0`

```bash
docker container run -d -p 5000:8888 --network strigus --env REDIS_HOST=myredis --name giropops-senhas isadora/linuxtips-giropops-senhas:1.0
```
