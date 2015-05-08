JHipster Example on Heroku
==========================

This is an example of a JHipster app that is ready to run on Heroku.

To deploy, do the following:

```sh-session
$ git clone
$ heroku create
$ heroku buildpacks:add https://github.com/heroku/heroku-buildpack-nodejs
$ heroku buildpacks:add https://github.com/heroku/heroku-buildpack-java
$ heroku config:set MAVEN_CUSTOM_OPTS="-Pprod -DskipTests=true"
$ git push heroku master
