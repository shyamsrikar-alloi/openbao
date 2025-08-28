#  Add the OpenBao Helm Repositor
```
helm repo add openbao https://openbao.github.io/openbao-helm
helm repo update
```
# Verify the chart is available:
```
helm search repo openbao/openbao
```
- This should display output similar to:
```
NAME            CHART VERSION   APP VERSION
openbao/openbao 0.4.0           v2.0.0-alpha20240329
```



# Install OpenBao Using Helm
```
helm install openbao openbao/openbao \
  --namespace rafay \
  --create-namespace \
  --set "server.ha.enabled=true" \
  --set "server.dataStorage.storageClass=gp2"
```


Default (Standalone) — single server, file storage (not production-ready):
```
helm install openbao openbao/openbao

```
Dev Mode — in-memory storage for testing:
```
helm install openbao openbao/openbao \
  --set "server.dev.enabled=true"
```
HA Mode — high availability, recommended for production:
```
helm install openbao openbao/openbao \
  --set "server.ha.enabled=true"

```
External Mode — integrates with an existing OpenBao instance:
```
helm install openbao openbao/openbao \
  --set "injector.externalVaultAddr=http://external-openbao:8200"
```



