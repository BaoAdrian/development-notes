# Docker Notes
Starting a single container
```
docker run [image]
docker run jboss/keycloak
```

Giving a container a name
```
docker run --name keycloak jboss/keycloak
```

`docker run` with port mapping
```
docker run -p [port:port]
docker run -p 8080:8080
```

`docker run` with environment variables
```
docker run -e [env_variable]
docker run -e KEYCLOAK_USER=admin -e KEYCLOAK_PASSWORD=ADMIN -e DB_VENDOR=H2 jboss/keycloak
```

`docker run` with volumes (see [volumes](https://docs.docker.com/storage/volumes/) and [bind-mounting](https://docs.docker.com/storage/bind-mounts/) docs)
```bash
# Volumes
docker run -v [vol_name:container_dest:optional_args]
docker run -v theme_vol:/opt/jboss/keycloak/themes/customTheme

docker run --mount type=volume source=theme_vol destination=/opt/jboss/keycloak/themes/customTheme

# Bind Mapping
docker run -v [host_dir:container_dest:optional_args]
docker run -v /opt/keycloak/customTheme:/opt/jboss/keycloak/themes/customTheme

docker run --mount type=bind source=/opt/keycloak/customTheme destination=/opt/jboss/keycloak/themes/customTheme
```

