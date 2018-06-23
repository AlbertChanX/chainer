

## IPFS

### run 

```
mkdir ipfs-export
mkdir ipfs-data

docker run -d --name ipfs-node \
  -v $(pwd)/ipfs-export:/export -v $(pwd)/ipfs-data:/data/ipfs \
  -p 8080:8080 -p 4001:4001 -p 127.0.0.1:5001:5001 \
  openthings/go-ipfs:latest

docker logs -f ipfs-node
docker-machine ip
docker exec -it ipfs-node /bin/sh
```

> view (http://localhost:5001/webui)


## Refer

1. [EOS contract](http://chainkr.pro/jishu/841.html)
2. [ipfs ](http://ipfser.org/)