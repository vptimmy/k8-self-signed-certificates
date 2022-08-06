# Self Signed CA and wildcard SSL Certificate

## Requirements
cert-manager


## Description
This will create a self signed CA as well as a wildcard certificate *.home.lab signed by the self signed ca.

## Install
`skaffold run`


## How to use with future ingresses
Simply append the annotation below to your metadata.  Once the ingress deploys an automatic ssl certificate will be created.
```
apiVersion: networking.k8.io/vi
kind: Ingress
metadata:
   annotations: cert-manager.io/cluster-issuer: homelab-ca-issuer 
```

## How to get the public crt to share
`kubectl -n cert-manager get secret homelab-ca -o jsonpath='{.data.ca\.crt}' | base64 -d > home.lab.crt`

## How to install the self signed certificate on Ubuntu 20.04
Copy the contents of the .crt file from above to /usr/local/share/ca-certificates then run the command `sudo update-ca-certificates`.

## How to install the self signed certificate on Andriod / IOS
Email the crt to yourself.  Open and install it automatically.

## How to install the self signed certificate on Windows
Google it :P
