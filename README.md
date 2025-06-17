# Dev blog

[![Netlify Status](https://api.netlify.com/api/v1/badges/97a94553-026d-40f4-8ab0-19e1619805f6/deploy-status)](https://app.netlify.com/projects/gniewomir-dev-blog/deploys)

### local setup

* Install Hugo 0.147.8
```shell
$ git clone git@github.com:gniewomir/dev.blog.git
$ cd dev.blog
$ git submodule update --init
$ hugo build
$ hugo server
```

### reference env 

```shell
$ lsb_release -a
```

```text
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 24.04.1 LTS
Release:	24.04
Codename:	noble
```

```shell
$ hugo version
```

```text
hugo v0.147.8+extended+withdeploy linux/amd64 BuildDate=2025-06-07T12:59:52Z VendorInfo=brew
```

### Ref 
* https://github.com/adityatelange/hugo-PaperMod/wiki
* https://gohugo.io/host-and-deploy/host-on-netlify/
