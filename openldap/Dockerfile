
FROM osixia/openldap

LABEL maintainer="you@example.org"

ENV LDAP_ORGANISATION="Example Organization" \
    LDAP_DOMAIN="example.org"

COPY bootstrap.ldif /container/service/slapd/assets/config/bootstrap/ldif/50-bootstrap.ldif
