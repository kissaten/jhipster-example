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
```

This application differs only slightly from the standard JHipster template.
Here's a summary of those changes:

#### src/main/resources/config/application-prod.yml

```yaml
spring:
  profiles:
    active: prod
    datasource:
      dataSourceClassName: org.postgresql.ds.PGSimpleDataSource
      cachePrepStmts: true
      prepStmtCacheSize: 250
      prepStmtCacheSqlLimit: 2048
      useServerPrepStmts: true
      jpa:
        database-platform: org.hibernate.dialect.PostgreSQL82Dialect
        database: POSTGRESQL
```

#### HerokuDatabaseConfiguration.java

The file `src/main/java/<your-package>/config/HerokuDatabaseConfiguration.java` is boilerplate.
Just copy it into your app.

#### pom.xml

```xml

<dependency>
  <groupId>org.postgresql</groupId>
  <artifactId>postgresql</artifactId>
  <version>${postgresql.version}</version>
</dependency>
```
