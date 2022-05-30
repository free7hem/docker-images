## docker compose configuration example
```
version: '3.3'
services:
    keycloak:
        image: camuscheung/keycloak
        environment:
            KEYCLOAK_ADMIN: admin
            KEYCLOAK_ADMIN_PASSWORD: changeme
            KC_DB_URL_HOST: mysql
            KC_DB_USERNAME: root
            KC_DB_PASSWORD: changeme
            KC_HOSTNAME: sso.hsichin.com
            KC_METRICS_ENABLED-enabled: 'true'
            KC_HTTP_ENABLED: 'true'
            KC_PROXY: 'edge'
        labels:
            - 'traefik.http.routers.sso.rule=Host(`sso.hsichin.com`)'
            - 'traefik.http.routers.sso.tls.certresolver=le'

networks:
    default:
        external: true
        name: traefik

```