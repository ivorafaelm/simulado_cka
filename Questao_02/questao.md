### Questão 02

Criar um service/ep apontando para um pod.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

```bash
kubectl run meu-pod --image nginx --port 80 --dry-run=client -o yaml > meu-pod.yaml

kubectl create -f meu-pod.yaml

kubectl expose pod meu-pod --name meu-service --type NodePort --dry-run=client -o yaml > meu-service.yaml

kubectl create -f meu-service.yaml
```

Os arquivos gerados pelo comando kubectl run foram versionados para facilitar o entendimento.

</details>