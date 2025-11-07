# Instruões Gerais Docker

Docker é uma plataforma Microsoft bastante popular que encapsula um servidor.
Dessa forma, é possível instalar e executar programas de forma a não prejudicar o sistema hospede.


# Capítulo I - criação de Containers


Criar container


Instalação do docker desktop

Se tiver a imagem instalada (“welcome to docker” p. ex.), executar. Ela vai pedir as opções. Preencher com a porta (8090, e.g.)

Acessar via localhost e porta.

PARA SABER EM QUE PORTA ESTÁ RESPONDENDO:

```python
docker ps

CONTAINER ID   IMAGE                  COMMAND                  CREATED             STATUS             PORTS                                 NAMES
0b6dcbf7a7f2   ollama/ollama          "/bin/ollama serve"      About an hour ago   Up About an hour   11434/tcp, 0.0.0.0:11436->11436/tcp   ollama4
```
a porta está mostrada na coluna "PORTS"


ou

```python
docker port ollama4
11436/tcp -> 0.0.0.0:11436
```

Baixar uma imagem e fazer a imagem

para baixar, por exemplo:

git clone https://github.com/docker/welcome-to-docker


ir para a pasta da imagem.

Editar o arquivo Dockerfile e incluir o que mais quiser.

e.g.

### Usando imagem bitnami
usa imagem bitnami mais enxuta debian
e instala utils que tem ping

FROM  bitnami/minideb:latest

RUN apt-get update && apt-get install -y iputils-ping

depois, para compilar:
```python
$ docker build -t my_custom_image .    <= atenção ao ponto “.”; se não, não compila
```
para executar:

```python
$ docker run -it my_custom_image
```
para mandar ao repositório e depois baixar e rodar em outro servidor:
Este primeiro comando coloca um tag na imagem. A maioria fica com o tag “latest”
docker tag my-image your-dockerhub-username/my-image:tag

Esse comando permite logar no Docker Hub.
docker login -u your-dockerhub-username

Se estiver usando o docker desktop, ele normalmente já está logado.

para mandar ao repositório.
docker push your-dockerhub-username/my-image:tag

Depois, no outro servidor, baixar:
docker pull your-dockerhub-username/my-image:tag

e rodar:
docker run [OPTIONS] your-dockerhub-username/my-image:tag



# CAPÍTULO II - Gerando Containers Específicos

