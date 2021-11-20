### Questão 03

Colocar um node para que não execute nenhum containers.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para incluir o taint para não permitir a execução de containers:

```bash
kubectl taint nodes node1 key1=value1:NoExecute
```

Para retirar o taint para não permitir a execução de containers:

```bash
kubectl taint nodes node1 key1=value1:NoExecute-

```
</details>