# README

Install fluxcd

```bash
curl -s https://fluxcd.io/install.sh | sudo bash
```

Add age public key

```bash
cat age.agekey | kubectl create secret generic sops-age --namespace=flux-system --from-file=age.agekey=/dev/stdin
```

Bootstrap

```bash
flux bootstrap git \
  --url=ssh://git@github.com/iamjadesmith/homelab.git \
  --branch=main \
  --private-key-file=<path/to/ssh/private.key> \
  --password=<key-passphrase> \
  --path=clusters/my-cluster
```

To watch the progress:

```bash
flux get kustomizations --watch
```
