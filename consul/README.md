# comandos

# create de docker: docker compose up -d

# entrar no containeir: docker exec -it consulserver01 sh

# dentro do container para iniciar o serviço:
# rode os seguintes comandos do consul
# iniciar o serviço: consul agent -dev
# em outro termianl: consul members (este comando mostra os ips dos membros do cluster criado)

# ver o catalogo: curl localhost:8500/v1/catalog/nodes

# apk -U add bind-tools => instala o dig
# dig @localhost -p 8600 ou dig @localhost -p 8600 consul01.node.consul => busca todos os nodes e ips dos mesmos no cluster


##############################################

# rodando tres servidores
# subir tres dockers com o consul
# entrar no docker
# ver o ip local do servidor com o comando ifconfig
# criar os diretorios rode: mkdir /var/lib/consul e mkdir /etc/consul.d 
# comando para subir o primeiro servidor: consul agent -server -bootstrap-expect=3 -node=consulserver01 -bind=172.21.0.4 -data-dir=/var/lib/consul -config-dir=/etc/consul.d 
# (ip retornado da pesquisa com o ifconfig)
# rode os comandos em outros terminais para os demais servidores

# fazer os servidores se conectarem
# comando: consul join ip (do servidor a conectar)



#######################################
# rodando client
# criar uma pasta com um nome qualquer dentro dela uma pasta especifica para o client
# criar os diretorios como acima
# consul agent -node=consulclient01 -bind=ip -data-dir=/var/lib/consul -config-dir=/etc/consul.d
# por padrão quando não indicamos se é um client ou server o consul cria um client
# usar o comando join para inserir o client no cluster


##############################3
# registrando um serviço 
# dentro da pasta para o client crie um arquivo .json
# apos criar o arquivo rode o comando: consul reload
# para ver o serviço criado instale o bind-tools usando o comando acima
# e rode o comando: dig @localhost -p 8600 nginx.node.consul