Para resolver el problema con systemd-resolved añadir en los servicios lo siguente:
--resolv-conf=/run/systemd/resolve/resolv.conf
systemctl daemon-reload
systemctl restart k3s