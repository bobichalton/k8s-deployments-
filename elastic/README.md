Usuario: elastic
Pass: kubectl get secret elastic-es-elastic-user -o=jsonpath='{.data.elastic}' | base64 --decode