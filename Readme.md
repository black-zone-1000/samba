# Samba

A [Docker](http://docker.com) file to build images for AMD & ARM devices with a installation of [Samba](https://www.samba.org/) that is the standard Windows interoperability suite of programs for Linux and Unix. This is my personal Multi-architecture docker recipe.


This is a modified distribution:
1. Support ARM
2. Supports force user and force group by parameters


## Thanks to

- [Samba](https://www.samba.org/)
- [dastrasmue rpi-samba](https://github.com/dastrasmue/rpi-samba)
- elswork (https://hub.docker.com/r/elswork/samba / https://www.github.com/DeftWork/samba )

## Details

- [GitHub](https://github.com/black-zone-1000/samba)

| Docker Hub | Docker Pulls | Docker Stars | Size/Layers |
| --- | --- | --- | --- |
| [samba](https://hub.docker.com/r/rdxmaster/samba "rdxmaster/samba on Docker Hub") | [![](https://img.shields.io/docker/pulls/rdxmaster/samba.svg)](https://hub.docker.com/r/rdxmaster/samba "rdxmaster/samba on Docker Hub") | [![](https://img.shields.io/docker/stars/rdxmaster/samba.svg)](https://hub.docker.com/r/rdxmaster/samba "rdxmaster/samba on Docker Hub") | [![](https://images.microbadger.com/badges/image/rdxmaster/samba.svg)](https://microbadger.com/images/rdxmaster/samba "rdxmaster/samba on microbadger.com") |

## Build Instructions

Build for amd64, armv7l, aarch64 architecture (thanks to its [Multi-Arch](https://blog.docker.com/2017/11/multi-arch-all-the-things/) base image)

``` sh
docker build -t rdxmaster/samba .
```

## Usage

I use it to share files between Linux and Windows, but it has many other capabilities. 

### Serve 

Start a samba fileshare.


``` sh
docker run -d -p 137:137/udp -p 138:138/udp -p 139:139 -p 445:445 -p 445:445/udp --hostname 'filer' -v /mnt/store/smb:/share/folder  rdxmaster/samba -u "your_username:your_password" -s "FileShare:/share/folder:rw:your_username"
``` 
On Windows point your filebrowser to `\\host-ip\FileShare` to preview site.

You can add -e FORCE_USER [user] -e FORCE_GROUP [group] to activate the force user and group
