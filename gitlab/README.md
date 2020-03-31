kubectl create secret generic smtp-password --from-literal=password=0a8bfdff24b7f5e2f8917220a8d2d397
helm template gitlab gitlab/gitlab --dry-run `
  --set global.hosts.domain=ithub.space `
  --set global.hosts.externalIP=35.205.122.35 `
  --set global.edition=ce `
  --set global.email.from=gitlab@ithub.space `
  --set global.email.reply_to=noreply@ithub.space `
  --set global.smtp.address=in-v3.mailjet.com `
  --set global.smtp.authentication=login `
  --set global.smtp.domain=in-v3.mailjet.com `
  --set global.smtp.enabled=true `
  --set global.smtp.password.secret=smtp-password `
  --set global.smtp.port=587 `
  --set global.smtp.starttls_auto=true `
  --set global.smtp.user_name=47968d33689c2e3d2089e3ad32cf569d `
  --set global.ingress.configureCertmanager=false `
  --set certmanager.createCustomResources=false `
  --set certmanager.install=false `
  --set nginx-ingress.enabled=false `
  --set prometheus.install=false `
  --set minio.replicas=1 `
  --set gitlab.gitlab-shell.replicaCount=1 `
  --set gitlab.unicorn.replicaCount=1 > gitlab.yaml
En gitlab.yaml:
Eliminar los tres ingress y copiar el contenido del archivo ingress.yaml
Cambiar todas las ocurrencias de *replicas: 2 a 1
Password inicial de la cuenta root:
kubectl get secret gitlab-gitlab-initial-root-password -ojsonpath='{.data.password}' | base64 --decode ; echo
Eliminar la posibilidad de crear cuentas:
Gitlab > Admin area > settings > General > Sign-up restrictions > remove the check mark “Signup enabled”