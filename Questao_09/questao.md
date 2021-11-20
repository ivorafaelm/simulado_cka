### Questão 09

Organizar a saída do comando "kubectl get pods" pelo tamanho do capacity storage.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

```bash
kubectl get pods --sort-by=.spec.capacity.storage --all-namespaces
```

</details>