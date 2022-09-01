Esse repositório contém alguns exemplos de como o Consul funciona para fazer service discovery (via API ou DNS) e health checks. O script docker irá criar uma rede no consul com 3 servidores e 2 clients. Os 3 servidores são responsáveis por fornecer informações sobre os serviços e máquinas disponíveis e os clients são exemplos de servidores que podem ser monitorados com o Consul. Ambos os clients tem o registro de um serviço chamado ``Nginx`` e o client01 tem um health check no serviço. Como o ``Nginx`` não está instalado/rodando nos clients, o serviço não passa no check e fica indisponível via service discovery. O client02 não tem health check, então o serviço do ``Nginx`` fica disponível.

As configurações dos servers/clients se encontram nas pastas ``clients/*.json`` e ``servers/*.json``

# Iniciando o projeto

**Cria a rede do consul com 3 servers e 2 clients**
```
docker-compose up -d
```

**Para acessar um dos containers**
```
docker-compose up -d
```

**Interface web do consul**
A interface web pode ser acessada em `http://localhost:8500/ui`

# Comandos Consul

**Ver máquinas registradas no Consul**
```
consul members
```

**Recarrega as configurações de um agent do consul (server ou client)**
```
consul reload
```

**Gera uma chave que pode ser usada para encriptografar a comunicação entre servers e clients consul**
```
consul key-gen
```

**Consulta as máquinas disponíveis via API**
```
curl localhost:8500/v1/catalog/nodes
```

**Consultar as máquinas disponíveis via DNS**
```
dig @localhost -p 8600 consulserver01.node.consul
```

**Consulta um serviço via DNS**
```
dig @localhost -p 8600 nginx.service.consul
```

**Consulta um serviço via console**
```
consul catalog nodes --service=nginx
```

**Lista de maneira detalhada os serviços disponíveis no consul via console**
```
consul catalog nodes --detailed
```
