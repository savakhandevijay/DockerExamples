### docker network
- Create docker network with defined subnet ip range. eg `docker network create --subnet=172.28.0.0/16 {network_name}`
- Docker Compose assigns the network name based on the current directory. eg if project dir is `staticIPAddress` then network name would be
`staticIPAddress_{network_name}` by default. to check docker network details use below command
`docker inspect --format='{{json .NetworkSettings.Networks}}' {network_name} | jq .`
- *issues*
    - sometime network already created in docker system, during previous build attemp.
    - once docker network created, it will assign IP address to its container, based on subnet range give or assigned to it.
    - alway check network is created before or not e.g `docker network ls`
    - do docker network inspect to check its IPAM config values e.g. `docker inspect network {network_name}`

### Static IP
    - Now we have defined our networks subnet by the `ipam` keyword and assigned IPv4_address to service.