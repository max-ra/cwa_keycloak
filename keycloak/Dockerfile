# Keycloak custom build for postgres
ARG KEYCLOAK_VERSION

FROM quay.io/keycloak/keycloak:${KEYCLOAK_VERSION} AS builder

# Configure database vendor
ARG KC_DB=postgres

# Configure health and metric support
ENV KC_HEALTH_ENABLED=false
ENV KC_METRICS_ENABLED=true

# Configure caching
#ENV KC_CACHE=local

# Configure Features
ARG KC_FEATURES

RUN /opt/keycloak/bin/kc.sh build

FROM quay.io/keycloak/keycloak:${KEYCLOAK_VERSION}
COPY --from=builder /opt/keycloak/ /opt/keycloak/

ENTRYPOINT ["/opt/keycloak/bin/kc.sh"]

