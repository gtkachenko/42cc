### Pre-requisites
 - Docker should be installed on the host machine
 - Access to the Internet
 - Clone repo [calc](https://github.com/jardev/calc)

### Build image and run container
1. Put Dockerfile in the same folder github[repo](https://github.com/jardev/calc) with calc python code
2. To build image please run command like:
```shell
    docker build -f Dockerfile -t calc:0.1 or
    docker build -f Dockerfile.multistage -t calc-multistage:0.1
```
3. To run container:
```shell
    docker run -p 127.0.0.1:8000:8000 calc:0.1 or
    docler run -p 127.0.0.1:8000:8000 calc-multistage::0.1 
```
