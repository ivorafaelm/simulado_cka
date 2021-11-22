### Questão 12

Fazer a instalação do nginx em determinada versão, atualizar e depois realizar o rollback com o --record.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para efetuar a criação do nginx em determinada versão podemos utilizar o seguinte comando:

```bash
kubectl create deployment meu-deployment --image=nginx:1.19 --dry-run=client -o yaml > meu-deployment.yaml
kubectl create -f meu-deployment.yaml
```

Para efetuar a alteração da versão do nginx podemos utilizar os seguintes passos: 

```bash
kubectl edit deployments.apps meu-deployment --record
```

Ou ainda: 
```bash
kubectl edit deployments.apps meu-deployment --record
kubectl set image deployment meu-deployment nginx=nginx:1.20 --record
```

E alterar o seguinte trecho do yaml:

De:
```yaml
spec:
      containers:
      - image: nginx:1.19
        imagePullPolicy: IfNotPresent
        name: nginx
        resources: {}
        terminationMessagePath: /dev/termination-log
        terminationMessagePolicy: File
      dnsPolicy: ClusterFirst
```

Para:
```yaml
spec:
      containers:
      - image: nginx:1.20
        imagePullPolicy: IfNotPresent
        name: nginx
        resources: {}
        terminationMessagePath: /dev/termination-log
        terminationMessagePolicy: File
      dnsPolicy: ClusterFirst
```

Após a edição do arquivo um novo pod será criado já com a versão nova do Nginx.

Para efetuar o rollback podemos efetuar o seguinte comando:

```bash
kubectl rollout undo deployment meu-deployment --to-revision 1
```

</details>