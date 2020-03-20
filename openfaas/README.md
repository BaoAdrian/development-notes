# OpenFAAS

# CLI Installation (Ubuntu 18.04)
Run provided script
```
curl -sSL https://cli.openfaas.com | sudo -E sh
```

Then it is recommended to pull templates
```
faas-cli template pull
```

# Creating functions
Since functions are pushed to Dockerhubs registry, login first by doing
```
docker login -u [username] -p [password] docker.io
```

Creating `golang` function in CWD
```
faas-cli new [function_name] --lang go
function_name.yml
./function_name/
./function_name/handler.go
```

Build Function
```
faas-cli build -f function_name.yml
```

Push Function to docker registry
```
faas-cli push -f function_name.yml
```

Deploy Function
```
faas-cli deploy -f function_name.yml
```

The above three steps can be combined into a single command using `up`
```
faas-cli up -f function_name.yml
```