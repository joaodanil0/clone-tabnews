# clone-tabnews

Projeto para exercitar programação

Estou rodando todo o sistema dentro de um docker container, e seu Dockerfile está em `infra/Dockerfile`.

Para compilar a imagem utilizei o comando:

```
docker build -t curso-dev infra/
```

Para criar a instância da imagem, usei o comando:

```
docker run --name curso-dev --network host -v ./workdir:/workspace -v /var/run/docker.sock:/var/run/docker.sock -it curso-dev
```

> --network host: Foi necessário para acessar o postgres (outro docker container). Esse comando utiliza a mesma inteface de rede do PC host.
> -v /var/run/docker.sock:/var/run/docker.sock: Foi necessário para que consiga rodar o docker dentro de um docker container
