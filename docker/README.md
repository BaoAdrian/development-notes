# Official Documentation
- [Docker](https://docs.docker.com/)
- [docker-compose](https://docs.docker.com/compose/)

# Docker Notes
Starting a single container
```
docker run [image]
docker run jboss/keycloak
```

Giving a container a name
```
docker run --name [name] ...
docker run --name keycloak jboss/keycloak
```

`docker run` with port mapping
```
docker run -p [port:port] ...
docker run -p 8080:8080 jboss/keycloak
```

`docker run` with environment variables
```
docker run -e [env_variable] ...
docker run -e KEYCLOAK_USER=admin -e KEYCLOAK_PASSWORD=ADMIN -e DB_VENDOR=H2 jboss/keycloak
```

`docker run` with volumes (see [volumes](https://docs.docker.com/storage/volumes/) and [bind-mounting](https://docs.docker.com/storage/bind-mounts/) docs)
```bash
# Volumes (using -v|--volume)
docker run -v [vol_name:container_dest:optional_args] ...
docker run -v theme_vol:/opt/jboss/keycloak/themes/customTheme jboss/keycloak

# Volumes (using --mount)
docker run --mount type=volume source=theme_vol destination=/opt/jboss/keycloak/themes/customTheme

# Bind Mapping (using -v|--volume)
docker run -v [host_dir:container_dest:optional_args] ...
docker run -v /opt/keycloak/customTheme:/opt/jboss/keycloak/themes/customTheme jboss/keycloak

# Bind Mapping (using --mount)
docker run --mount type=bind source=/opt/keycloak/customTheme destination=/opt/jboss/keycloak/themes/customTheme jboss/keycloak
```

Basic Operations
```
docker [start|stop|rm|restart|...] [service]
```

Enter container
```
docker exec -it [service] bash
docker exec -it keycloak bash
```

Execute command inside container
```bash
docker exec -it [service] [command]
docker exec -it keycloak /opt/jboss/keycloak/bin/kcadm.sh config credentials --server http://localhost:8080/auth --realm master --user admin --password admin

# OR more complex, multi-part commands
docker exec -it keycloak bash -c '/opt/jboss/keycloak/bin/kcadm.sh config credentials --server http://localhost:8080/auth --realm master --user admin --password admin && /opt/jboss/keycloak/bin/kcadm.sh update realms/master -s sslRequired=NONE'
```

# Docker Compose Notes
Start services 
```
docker-compose build
docker-compose up
OR
docker-compose up --build
```

Build with no cache (handy when wanting to do a full wipe rebuild)
```
docker-compose build --no-cache
```

Start services provided by alternate compose file
```
docker-compose -f [compose_file] [command]
docker-compose -f docker-compose.prod.yml up --build
```

Basic Operations
```
docker-compose [start|stop|rm|restart|...] [service]
```

Enter container
```
docker-compose exec -it [service] bash
docker-compose exec -it postgres bash
```

Execute command inside container
```
docker-compose exec -it [service] [command]
docker-compose exec -it postgres ls -la
```

