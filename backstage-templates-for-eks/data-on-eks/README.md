## Credential Setup

Create an AWS Secret on required namespaces for deploying templates on AWS environment using below commands:

```bash
# AWS Credentials for data-on-eks Namespace
cat << EOF > ./aws-secrets-doeks.yaml
---
apiVersion: v1
kind: Secret
metadata:
  name: aws-credentials
  namespace: data-on-eks
type: Opaque
data:
  AWS_ACCESS_KEY_ID: ${IDP_AWS_ACCESS_KEY_ID_BASE64}
  AWS_SECRET_ACCESS_KEY: $IDP_AWS_SECRET_ACCESS_KEY_BASE64
EOF
kubectl apply -f ./aws-secrets-doeks.yaml
```

For `EKS Observability` templates, the default namespace is in fact `data-tf-eks-observability` as also set on the snippet above. If you choose a different namespace, you need to edit the namespace in the above secret.