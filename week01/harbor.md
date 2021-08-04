# Harbor Installation

### Harbor Installation Prerequisites

##### Hardware

Resource |Minimum |Recommended
:----|:----|:----
CPU	|2 CPU |4 CPU
Mem	|4 GB |8 GB
Disk |40 GB |160 GB

##### Software

Software |Version |Description
:----|:----|:----
Docker engine	|Version 17.06.0-ce+ or higher	|For installation instructions, see Docker Engine documentation
Docker Compose	|Version 1.18.0 or higher	|For installation instructions, see Docker Compose documentation
Openssl	|Latest is preferred	|Used to generate certificate and keys for Harbor

##### Network ports

Port |Protocol |Description
443	|HTTPS	|Harbor portal and core API accept HTTPS requests on this port. You can change this port in the configuration file.
4443 |HTTPS	|Connections to the Docker Content Trust service for Harbor. Only required if Notary is enabled. You can change this port in the configuration file.
80 |HTTP |Harbor portal and core API accept HTTP requests on this port. You can change this port in the configuration file.



### Install Harbor

- Download Package

```
wget https://github.com/goharbor/harbor/releases/download/v2.3.1/harbor-online-installer-v2.3.1.tgz
```

- extract the installer package

```
tar xzvf harbor-online-installer-v2.3.1.tgz
```

- Generate a Certificate Authority Certificate

```
cd harbor
mkdir certs
openssl genrsa -out certs/ca.key 4096
openssl req -x509 -new -nodes -sha512 -days 3650 \
 -subj "/C=TW/ST=Taipei/L=Taipei/O=Harbor/OU=IT/CN=harbor.example.com" \
 -key certs/ca.key \
 -out certs/ca.crt
```

- Generate a Server Certificate

```
openssl genrsa -out certs/harbor.example.com.key 4096
openssl req -sha512 -new \
    -subj "/C=TW/ST=Taipei/L=Taipei/O=Harbor/OU=IT/CN=harbor.example.com" \
    -key certs/harbor.example.com.key \
    -out certs/harbor.example.com.csr
openssl x509 -req -sha512 -days 3650 \
    -CA ca.crt -CAkey ca.key -CAcreateserial \
    -in certs/harbor.example.com.csr \
    -out certs/harbor.example.com.crt
```

- Configure the Harbor YML File

```
cp harbor.yml.tmpl harbor.yml
```

```
vi harbor.yml
---
hostname: harbor.example.com
---
https:
  port: 443
  certificate: /root/harbor/certs/harbor.example.com.crt
  private_key: /root/harbor/certs/harbor.example.com.key
```

- Run the Installer Script

```
./install.sh
```



### Deploying Harbor with High Availability via Helm

https://github.com/goharbor/harbor-helm