## Inventory

Copy the example inventory and adjust it for your environment:

```bash
cp ansible/inventory/hosts.example.ini ansible/inventory/hosts.ini
```

#nextcloud
1. Get the nextcloud URL by running:

```bash
  export POD_NAME=$(kubectl get pods --namespace nextcloud -l "app.kubernetes.io/name=nextcloud" -o jsonpath="{.items[0].metadata.name}")
  echo http://127.0.0.1:8080/
  kubectl port-forward --namespace nextcloud $POD_NAME 8080:80
```

2. Get your nextcloud login credentials by running:

```bash
  echo User:     admin
  echo Password: $(kubectl get secret --namespace nextcloud nextcloud -o jsonpath="{.data.nextcloud-password}" | base64 --decode)
```