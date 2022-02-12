## Requirements
Deploy Heroku

To deploy my backend, I did the following procedure:

`Add the commands used here, sequentially.`

```
$ heroku login
$ heroku create --remote hawkins stranger-things
$ heroku create --remote upside-down stranger-things-up-down
$ heroku config:set upsideDown="false" --app stranger-things
$ heroku config:set upsideDown="true" --app stranger-things-up-down
$ git add .
$ git commit -m "Requirement 6"
$ git push stranger-things pedro-tofani:master
$ git push stranger-things-up-down pedro-tofani:master
```

### 7 - Monitoring

To be able to monitor my API, I did the following procedure:

`Add the commands used here, sequentially.`

```
heroku config:set PM2_PUBLIC_KEY=PUBLIC_KEY PM2_SECRET_KEY=PRIVATE_KEY PM2_MACHINE_NAME=pedro-pc --app stranger-things
heroku config:set PM2_PUBLIC_KEY=PUBLIC_KEY PM2_SECRET_KEY=PRIVATE_KEY PM2_MACHINE_NAME=pedro-pc-1 \
-- stranger-things-up-down app
```
