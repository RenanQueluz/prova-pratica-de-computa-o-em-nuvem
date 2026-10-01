#prova 1 de computação  em nuvem
nome: Renan Augusto ulyas queluz
ra: e7513dfae53696704la


#o que eu fiz
Executei uma aplicação web em um container docker chamado loja.
Usei a imagem nginx:alpine e a porta 8081 do ambiente.

#verificação do container
 docker run -d --name loja -p 8081:80 nginx:alpine
Unable to find image 'nginx:alpine' locally
alpine: Pulling from library/nginx
e2de96513ba9: Pull complete 
d9aae54b5831: Pull complete 
6c53d0b2a666: Pull complete 
745dfb2690dd: Pull complete 
9a9a644fdd6a: Pull complete 
64c8194480fe: Pull complete 
e76228b47809: Pull complete 
e72112c14215: Pull complete 
Digest: sha256:df221db836e1754089190208cee7eeda94f233197056426eda74a43ab1abeac2
Status: Downloaded newer image for nginx:alpine
4ae0f250e073a184805cc815a1d3f14c96d7775cf43d1a438eb6c4e0c6c428ff
root@ubuntu:~$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                     NAMES
4ae0f250e073   nginx:alpine   "/docker-entrypoint.…"   34 seconds ago   Up 34 seconds   0.0.0.0:8081->80/tcp, [::]:8081->80/tcp   loja
root@ubuntu:~$ docker cp index.html loja:/usr/share/nginx/html/index.html
Successfully copied 2.05kB to loja:/usr/share/nginx/html/index.html
root@ubuntu:~$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                     NAMES
4ae0f250e073   nginx:alpine   "/docker-entrypoint.…"   7 minutes ago   Up 7 minutes   0.0.0.0:8081->80/tcp, [::]:8081->80/tcp   loja
root@ubuntu:~$ curl http://localhost:8081
<!DOCTYPE html>
<html lang='pt-BR'
<head>
   <meta charset="UTF-8"
   <title>Loja </title>
</head>
<body>
   <h1> loja no ar </h1>
</body>
</html>


#explicação
com minhas palavras, qual é a  diferença entre nginx:alpine
e o container loja? para que serviu o mapeamento 8081:80 

resposta: o nginx:alpine serve apenas para criarmos a nossa imagem docker, e o container tera todo o nosso conteudo index.html, o mapeamento 8081:80 s
serve para conectar o nosso container que é 8081 pra dentro da porta docker :80
