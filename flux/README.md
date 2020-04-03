Instalar fluxctl: sudo snap install fluxctl --classic
Crear namespace: kubectl create -f namespace.yaml
Crear un access token en gitlab: https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html#creating-a-personal-access-token
Crear el config map con el token creado en el punto anterior:
kubectl create secret generic flux-git-auth --from-literal=GIT_AUTHUSER=flux --from-literal=GIT_AUTHKEY=TJPneoN8txk9CMziv1yz
Instalar flux en kubernetes:
fluxctl install \
--git-user=flux} \
--git-email=flux@users.noreply.github.com \
--git-url=--git-url=https://flux:TJPneoN8txk9CMziv1yz@gitlab.ithub.space/flux/demos.git \
--git-path=namespaces,workloads \
--namespace=flux | kubectl apply -f -