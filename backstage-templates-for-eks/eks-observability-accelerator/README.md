## Credential Setup

Create an AWS Secret on required namespaces for deploying templates on AWS environment using below commands:

```bash
# AWS Credentials for tf-eks-observability Namespace
cat << EOF > ./aws-secrets-eobs.yaml
---
apiVersion: v1
kind: Secret
metadata:
  name: aws-credentials
  namespace: tf-eks-observability
type: Opaque
data:
  AWS_ACCESS_KEY_ID: ${IDP_AWS_ACCESS_KEY_ID_BASE64}
  AWS_SECRET_ACCESS_KEY: $IDP_AWS_SECRET_ACCESS_KEY_BASE64
EOF
kubectl apply -f ./aws-secrets-eobs.yaml
```

For `Data-on-EKS` templates, the default namespace is in fact `data-on-eks` as also set on the snippet above. If you choose a different namespace, you need to edit the namespace in the above secret.