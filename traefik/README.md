Cambiar el contenido del archivo por el que esta en este directorio
/var/lib/rancher/k3s/server/manifests/traefik.yaml
systemctl restart k3s

Para dejar solo TLS v1.2 y v1.3
Añadir el contenido del archivo tls-options.yaml debajo del apartado por el que empieza el archivo
con: kubectl edit cm traefik -n kube-system