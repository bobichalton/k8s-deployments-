helm template gitlab gitlab/gitlab --set global.ingress.annotations."kubernetes\.io/tls-acme"=true --dry-run --values values.yaml > gitlab.yaml
En gitlab.yaml:
Eliminar los tres ingress y copiar el contenido del archivo ingress.yaml
Cambiar todas las ocurrencias de *replicas: 2 a 1
Password inicial de la cuenta root:
kubectl get secret gitlab-gitlab-initial-root-password -ojsonpath='{.data.password}' | base64 --decode ; echo
Eliminar la posibilidad de crear cuentas:
Gitlab > Admin area > settings > General > Sign-up restrictions > remove the check mark “Signup enabled”