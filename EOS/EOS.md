
## EOS

### run
> 因为eosio/eos镜像没有包含合约开发所需要的依赖包（这是by design的，为了镜像容量小的目的），
所以需要使用`eosio/eos-dev`镜像。这个镜像包含了用eosiocpp编译合约所需要的二进制文件和依赖包。

```
docker pull eosio/eos

docker run --name eosd -p 8888:8888 -p 9876:9876 -t eosio/eos nodeosd.sh

# in Windows
curl http://192.168.99.100:8888/v1/chain/get_info

```

### tools 

>-Cleos，Client EOS 它是一个命令行程序。在前端使用EOS是通过Cleos输入命令，给EOS下达指令。

-Nodeos，Node EOS 其实它就是挖矿客户端。在启动Nodeos之后，它自然就会产生区块。

-Keosd，它是在后端启动。它的目的主要是管理钱包，可以创建私钥。

### Wallet Management

```

Cleos wallet create -n {mywallet}

cleos create key

# import key to wallet
cleos wallet import {pk} -n {mywallet}

cleos wallet keys
```

* create account/user
```
cleos createaccount eosio ${new_account} ${owner_key} ${active_key}
```

> 其中eosio是超级用户，需要靠超级用户来创建其它的新用户，eosio后面就是你的新用户的用户名。
除了新的账号之外，命令后面还有两个key：

1、Owner key

2、Active key

Owner key是什么意思呢？`Owner key`表示分配给新账号的一个Owner认证的公钥。`Active key`是分配给新账号一个Active认证的一个公钥。

### Contract Deployment
```
$ cleos set contract eosio build/contracts/eosio.bios -p eosio
```
> 其中，eosio是要部署的账号，就是你用哪个账号去部署智能合约；

build/contracts/eosio.bios表示的是路径；

eos.bios是生成一个智能合约的目录。


## Reference
1. [EOS Contract](http://chainkr.pro/jishu/841.html)

2. [EOS - HelloWorld](https://blog.csdn.net/itleaks/article/details/80461917)