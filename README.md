# knowledge-docker
Docker file for knowledge

- This is Dockerfile that can build a docker image of [Knowledge](https://github.com/support-project/knowledge).


## Build yourself

Get DockerFile and run this command.

```
docker build -t knowledge .
mkdir ~/home/hoge/knowledge
chmod a+w /home/hoge/knowledge
docker run -d -p 80:8080 -v /home/hoge/knowledge:/root/.knowledge --name knowledge knowledge
```

## Setting

Make `volumes/knowledge` directory and `custom_connection.xml`

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<connectionConfig>
	<name>custom</name>
	<driverClass>org.postgresql.Driver</driverClass>
	<URL>jdbc:postgresql://db/knowledge_production</URL> 
	<user>postgres</user>
	<password>admin123</password>
	<schema>public</schema>
	<maxConn>0</maxConn>
	<autocommit>false</autocommit>
</connectionConfig>
```


## Run local

```
cp docker-compose.local.yml docker-compose.yml
docker-compose up -d
```

## Run prod

```
cp docker-compose.prod.yml docker-compose.yml
docker-compose up -d
```

