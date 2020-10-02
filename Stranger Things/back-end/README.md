

## Requisitos

### 6 - Deploy Heroku

Para realizar o deploy do meu backend, fiz o seguinte procedimento:

`Adicione aqui os comandos utilizados, de maneira sequencial.`

```
$ heroku login
$ heroku create --remote hawkins stranger-things
$ heroku create --remote upside-down stranger-things-up-down
$ heroku config:set upsideDown="false" --app stranger-things
$ heroku config:set upsideDown="true" --app stranger-things-up-down
$ git add .
$ git commit -m "Requisito 6"
$ git push stranger-things pedro-tofani:master
$ git push stranger-things-up-down pedro-tofani:master
```

### 7 - Monitoramento

Para conseguir realizar o monitoramento da minha API, fiz o seguinte procedimento:

`Adicione aqui os comandos utilizados, de maneira sequencial.`

```
heroku config:set PM2_PUBLIC_KEY=CHAVE_PUBLICA PM2_SECRET_KEY=CHAVE_PRIVADA PM2_MACHINE_NAME=pedro-pc --app stranger-things
heroku config:set PM2_PUBLIC_KEY=CHAVE_PUBLICA PM2_SECRET_KEY=CHAVE_PRIVADA PM2_MACHINE_NAME=pedro-pc-1 \
--app stranger-things-up-down
```
