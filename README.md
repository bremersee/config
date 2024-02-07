# config
Spring Cloud Config Server's Repo

Hint: application.yml is shared between all clients

Possible solution:
Use an uri with placeholder: https://github.com/bremersee/{application}
and store in the repo of the services two files 
{application}.yml for prod with label 'master' or 'main'
and {application}-dev.yml for development with label 'development'

If develop is merged into master, the config will be uptodate.

```
spring:
  profiles:
    active: composite
  cloud:
    config:
      server:
        composite:
        -
          type: git
          uri: https://github.com/bremersee/{application}
        -
          type: git
          uri: https://github.com/bremersee/config # for all
```

Will this work?

