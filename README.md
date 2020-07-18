# Openldap server + phpldapadmin server + Docker Compose running with auto generate/renew Let's Encrypt Certificate


## PREREQUISITES

In order to use this compose file (docker-compose.yml) you must have:

- docker https://docs.docker.com/engine/installation/
- docker-compose https://docs.docker.com/compose/install/
- docker-compose-letsencrypt-nginx-proxy-companion https://github.com/evertramos/docker-compose-letsencrypt-nginx-proxy-companion

## HOW TO USE 

1. Close this repository

```bash
$ git clone https://github.com/bowen31337/openldap-phpldapadmin-docker-letsencrypt.git
```

2. Make a copy of the `.env.example` and rename it to `.env`:

```bash
cp .env.example .env
```

Update this file with your preferences.


4. Start the container.

During the build time, the environment variables are injected into the image.

```bash
$ docker-compose up -d
```
5. test Ldap server
```bash
docker exec ldap-server-container ldapsearch -x -H ldap://localhost -b dc=example,dc=org -D "cn=admin_gh,dc=example,dc=org" -w admin_gh@example
docker exec ldap-server-container ldapsearch -x -H ldap://localhost -b dc=example,dc=org -D "cn=developer,dc=example,dc=org" -w developer@example
docker exec ldap-server-container ldapsearch -x -H ldap://localhost -b dc=example,dc=org -D "cn=maintainer,dc=example,dc=org" -w maintainer@example
```
the result should be
```
# extended LDIF
#
# LDAPv3
# base <dc=example,dc=org> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# search result
search: 2
result: 32 No such object

# numResponses: 1
```