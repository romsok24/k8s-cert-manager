## Source docummentation
Cert-manager project:<br>
https://cert-manager.io/docs/tutorials/acme/ingress/#step-5-deploy-cert-manager

AzureDNS docs<br>
https://cert-manager.io/docs/configuration/acme/dns01/azuredns/#service-principal

Preferred ACME challenge: dns-01 ( as there is no need for public ingres exposing )

## Installation steps

 - run: ```dns-01/dnschallenge_SP_create.sh```

 - run: ```kubectl apply -f  https://github.com/jetstack/cert-manager/releases/latest/download/cert-manager.yaml```

 - update ```hostedZoneName``` in ```dns-01/k8s-certmgr-le-prod-dns01-clissuer.yaml``` acordingly

 - run: ```kubectl apply -f dns-01/k8s-certmgr-le-prod-dns01-clissuer.yaml```
 
 - add this annotations to ingress instances:
  ```
    metadata:
      annotations:
        cert-manager.io/cluster-issuer: le-prod-dns-clisr
  ```