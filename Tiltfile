#!/usr/bin/env python

load('ext://helm_resource', 'helm_resource', 'helm_repo')
load('ext://secret', 'secret_create_generic', 'secret_from_dict')

# docker_build(
#     ref='keycloak:local',
#     context=".",
#     dockerfile="./loadTheme.Dockerfile"
# )

secret_create_generic(
    'realm-secret',
    from_file='realm.json=./realm-config/my-realm.json',
    namespace='default'
)

helm_resource(
    name='my-keycloak',
    chart='bitnami/keycloak',
    namespace="default",
    # image_deps=['keycloak:local'],
    # image_keys=[('image.registry', 'image.repository', 'image.tag')],
    # port_forwards=['8080:8080'],
    flags=["--values", "./values.yaml"]
)

# kubectl create secret generic realm-secret --from-file=./realm-config/realm-export.json -n keycloak
# secret_create_generic(
#     'realm-secret',
#     from_file='realm.json=./realm-config/realm-export.json',
#     namespace='keycloak'
# )

# k8s_yaml(secret_from_dict(
#     name='gitlab-client-secret',
#     namespace="keycloak",
#     inputs = {
#         'GITLAB_CLIENT_SECRET': '2aQvPFgdQcq8GFrcFmWh7dBHtrDYiCvX'
#     }
# ))

# helm_resource(
#     name='keycloak',
#     chart='codecentric/keycloak',
#     namespace="keycloak",
#     flags=[
#         "--values", "./values-codecentric.yaml",
#         "--version", "18.2.1"
#     ]
# )
