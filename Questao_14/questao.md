### Questão 14

Identificar quais pods fazem parte de determinado services.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

```bash
kubectl create deployment meu-deployment --image=nginx --port 80 --replicas=5
kubectl expose deployment meu-deployment --type NodePort

kubectl get services -o wide

# A saída será algo como:                                                 
NAME             TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE   SELECTOR
kubernetes       ClusterIP   10.96.0.1       <none>        443/TCP        35d   <none>
meu-deployment   NodePort    10.99.174.212   <none>        80:31423/TCP   16s   app=meu-deployment

# Para filtrar os pods é possível utilizar o mesmo seletor que está presente na saída acima:

kubectl get pods --selector=app=meu-deployment -o=name

# A saída será algo como: 

pod/meu-deployment-79c974d696-9jl7s
pod/meu-deployment-79c974d696-ckt9q
pod/meu-deployment-79c974d696-nkg6t
pod/meu-deployment-79c974d696-rlr6x
pod/meu-deployment-79c974d696-zbhtq

```

</details>