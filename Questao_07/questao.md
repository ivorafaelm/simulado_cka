### Questão 07

Criar um deployment do nginx com 5 réplicas.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

```bash
kubectl create deployment meu-deployment --image=nginx --replicas=5 --dry-run=client -o yaml > meu-deployment.yaml

kubectl create -f meu-deployment.yaml
```

O arquivo meu-deployment.yaml foi versionado para facilitar o entendimento.

</details>