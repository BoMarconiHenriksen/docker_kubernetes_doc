# Certificate Config File
cartificate.yaml  
```
apiVersion: certmanager.k8s.io/v1alpha1
kind: Certificate
metadata:
  name: ngc3-dk-tls
spec:
# This is where our secret is stored when it's abtained by cert manager
  secretName: ngc3-dk
  # Reference to the issuer.yaml
  issuerRef:
    name: letsencrypt-prod
    kind: ClusterIssuer
  # This is put on the certificate in bold letters. The cert. is good for this domain
  commonName: ngc3.rm-group.dk
  # List of domain names that is associated with this certificate
  dnsNames:
    - ngc3.rm-group.dk
    - www.ngc3.rm-group.dk
  acme:
    config:
      - http01:
          ingressClass: nginx
        # The verification process is going to try to access to make sure we have access to the listed domaine names
        domains:
          - ngc3.rm-group.dk
          - www.ngc3.rm-group.dk
```
