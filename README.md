# Adicionar o nginx no host

```
sudo nano /etc/hosts
```

Verificar o IP do container `reverse` que é o nginx. Em seu docker-compose, o ip foi fixado em `11.5.0.2`. Esse endereço naõ deve mudar podendo ficar no host.

Adicionado:

```
12.5.0.2 proxy.example.com
```


# Obter o IP do proxy

```
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps --filter name=reverse -q)
```

# IP docker

```
ip addr show docker0
```

# Host docker

```
getent hosts host.docker.internal
```

Se não existir, criar `127.17.0.1 host.docker.internal`, conforme `ip addr show docker0`.

# Verificar porta

```
netstat -tulpn
```