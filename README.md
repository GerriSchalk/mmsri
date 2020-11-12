# MMS Reference Implementation
[![Language grade: Java](https://img.shields.io/lgtm/grade/java/g/Open-MBEE/mms.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/Open-MBEE/mms/context:java) [![CircleCI](https://circleci.com/gh/Open-MBEE/mms.svg?style=svg)](https://circleci.com/gh/Open-MBEE/mms)

This is the reference implementation for MMS. For the source code, please head to [https://github.com/Open-MBEE/mms](https://github.com/Open-MBEE/mms). For more information about Open-MBEE, visit the [Open-MBEE Website](https://openmbee.org/).

## Quick Start
### Docker
Installation instructions are found here: [Docker documentation](https://docs.docker.com/)

1. Copy the `application.properties.example` file in `src/main/resources/` as `application.properties`
1. In the command line, run `docker-compose up --build` to create and start all the services from the configuration. 
1. Swagger ui at [http://localhost:8080/v3/swagger-ui.html](http://localhost:8080/v3/swagger-ui.html)
1. Use the command `docker-compose down` to stop any containers from running and to remove the containers, networks, and images created by the `docker-compose up` command. This command should always be done before any new attempts to restart the services from the configuration. 

Note the docker compose file is running the application with the `test` profile, with the config from `src/main/resources/application-test.properties`

This implementation brings in Spring Actuator and Logbook for monitoring and logging features - see [Logbook](https://github.com/zalando/logbook) and [Actuator](https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-features.html) for more info. 

The `application.properties.example` file has the suggested configs and comments. [example](https://github.com/Open-MBEE/mmsri/blob/develop/src/main/resources/application.properties.example)

## Using externalized configs
There are a variety of options to override the packaged config depending on the deployment scenario. See [Config locations](https://docs.spring.io/spring-boot/docs/current/reference/html/spring-boot-features.html#boot-features-external-config) for the list of options. Usually using profiles or environment variables are a good way to specify different configs for different environments.

## Developer Setup
### Docker 
We suggest using Docker to set up PostgreSQL and Elasticsearch.  Installation 
instructions are found here: [Docker documentation](https://docs.docker.com/)

### Java SE Development Kit 11
Installation instructions: [JDK-11 download](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)

### Postgresql
Install postgres (PostgreSQL) 11, instructions for Docker: [PostgreSQL with Docker](https://hub.docker.com/_/postgres)

    docker run -d -e POSTGRES_PASSWORD=test1234 -e POSTGRES_USER=mmsuser -e POSTGRES_DB=mms -p 5432:5432 postgres:11-alpine
    
### or Mysql
5.7 [Mysql Docker](https://hub.docker.com/_/mysql/)

    docker run -d -e MYSQL_ROOT_PASSWORD=test1234 -e MYSQL_DATABASE=mms -p 3306:3306 mysql:5.7

### Elasticsearch
Install Elasticsearch 7.8.  If you use Docker instructions are available here: [Setting up Elasticsearch with Docker](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html)

    docker run -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.8.1

### Artifact Storage
Use MinIO for an open sourced local s3 api compatible storage

    docker run -p 9000:9000 -e "MINIO_ACCESS_KEY=admintest" -e "MINIO_SECRET_KEY=admintest" minio/minio server /data
    
### The Application:
1. Copy the `application.properties.example` file in `src/main/resources/` as `application.properties`
1. Change values for all the appropriate properties. The example file holds sane values for most properties.
1. Setup Run and Debug configurations. The command line run command is `./gradlew bootRun`
1. Swagger ui at [http://localhost:8080/v3/swagger-ui.html](http://localhost:8080/v3/swagger-ui.html)

## Swagger codegen

[Gradle Plugin](https://github.com/int128/gradle-swagger-generator-plugin)

        ./gradlew generateSwaggerCode
        
Results in build/swagger-code-*

## Built With

* [Spring](https://spring.io)


## Contributing

To learn how you can get involved in a variety of ways, please see [Contributing to OpenMBEE](https://www.openmbee.org/contribute).

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/Open-MBEE/mms-sdvc.git). 


## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details



