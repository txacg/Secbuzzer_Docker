# SecBuzzer on Docker Tutorial :+1:

*Contributor: Lucas Ko ,YuPing Wang*


## Installation Docker

- Ubuntu : https://docs.docker.com/engine/installation/linux/ubuntulinux/
- Mac : https://docs.docker.com/docker-for-mac/
- Windows : https://docs.docker.com/docker-for-windows/

## Installation Environment - Ubuntu

```
$ curl -sSL https://get.docker.com/ | sh
```

```
$ sudo usermod -aG docker username
```


	restart virtual machine/computer

### Download
You can clone the file by using the git address shown above:

    git clone https://github.com/YuPing0612/secbuzzer.git

If you can't or don't want to install git, there is a link above to download
the contents of this repository as a zip file.

### Prepare Three Docker Images:

 * Elasticsearch 1.4
 * Mysql
 * Crawler



>### Build Elasticsearch 1.4.0 Image
```
$ cd secbuzzer/es1.4/
```
```
$ docker build -t elasticsearch:1.4.0 .
```
>### Build Mysql Image
```
$ docker pull mysql:latest
```
>### Build Crawler Image (base on jdk-8 images)
>edit properties.xml:

>```
><entry key="host">ip address</entry>

><entry key="logCarving_host">ip address</entry>

><entry key="mysql_host">ip address</entry>

><entry key="es_host">ip address</entry>
>```

>```
>$ cd secbuzzer/crawler/
>```
>```
>$ docker build -t crawler:1.0 .
>```

### docker-compose up

```
$ cd secbuzzer/
```
```
$ docker-compose up
```