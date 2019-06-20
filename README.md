# docker-NtopMikrotik

Docker image with NTOPNG and instructions for Mikrotik traffic-flow setup.

## Docker:
```bash
docker build . --tag=ntop

docker run \
  --name ntop \
  -d \
  -p 1234:1234 \
  -p 2055:2055/udp \
  -p 3000:3000 
  -v config:/etc/ntopng \
  -v date:/var/lib/ntopng \  
  ntop -m 
  ```

## Docker Hub:
```bash
docker run \
  --name ntop \
  -d \
  -p 1234:1234 \
  -p 2055:2055/udp \
  -p 3000:3000 \
  -v config:/etc/ntopng \
  -v date:/var/lib/ntopng \
  liujinbao3000/ntopmikrotik -m
```

## RouterOS:
```ros
/ip traffic-flow set active-flow-timeout=1m enabled=yes
/ip traffic-flow target add dst-address=[ntop-ip] port=2055 v9-template-timeout=1m
```

## References:
* ntop - https://www.ntop.org
* Docker - https://www.docker.com
* Mikrotik - https://mikrotik.com
