### Questão 18

Subir um pod com afinidade de node.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para esta questão é necessário escolher algum tipo de seletor para que o schedule seja possível.

Neste caso foi escolhido utilizar o label criado pela questão 17, desta forma temos os passos abaixo:

```bash
kubectl label nodes <node-name> disktype=ssd
kubectl run meu-pod --image nginx --dry-run=client -o yaml > meu-pod.yaml
```

O arquivo meu-pod.yaml foi alterado para conter o campo nodeSelector. Abaixo segue o arquivo alterado:

```yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: meu-pod
  name: meu-pod
spec:
  containers:
  - image: nginx
    name: meu-pod
    resources: {}
  nodeSelector:
    disktype: ssd
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}
```

Obs. Se o label não for criado previamente o pod não irá funcionar, pois ficará pendente de criação por violação de afinidade com os hosts.

</details>