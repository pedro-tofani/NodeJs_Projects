
## Requisitos

### 9 - Deploy Heroku

Para realizar o deploy do meu frontend, fiz o seguinte procedimento:

`Adicione aqui os comandos utilizados, de maneira sequencial.`

```
$ heroku create --remote heroku-st front-st --buildpack mars/create-react-app

$ heroku config:set REACT_APP_normalWorld=https://stranger-things.herokuapp.com/ REACT_APP_upsideDown=https://stranger-things-up-down.herokuapp.com/ REACT_APP_timeout=30000 --app front-st

$ git add .
$ git commit -m "Requisito 9"
$ git push heroku-st pedro-tofani:master

```

