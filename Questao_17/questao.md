### Questão 16

Adicionar um label no node.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para listar todos os labels de um nó existente:

```bash
# Para todos os nós do cluster
kubectl get nodes --show-labels

# Para um nó específico
kubectl get nodes <node-name> --show-labels

```

Para adicionar um label a um nó existente:

```bash
# Para adicionar um label com a informação disktype=ssd
kubectl label nodes <node-name> disktype=ssd

```

</details>