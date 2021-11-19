### Questão

Criar um pod com um volume não persistente.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

```bash
kubectl run meu-pod --image nginx --dry-run=client -o yaml > meu-pod.yaml

kubectl create -f meu-pod.yaml
```

O arquivo gerado pelo comando kubectl run foi versionado para facilitar o entendimento.

</details>