### Questão 22

Declarar a variável NGINX_PORT no env do container.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Efetuar a criação de um pod normalmente, conforme já vimos nas questões anteriores.

```bash
kubectl run meu-pod --image nginx --port 80 --dry-run=client -o yaml > meu-pod.yaml
```

Após a criação do arquivo basta incluir o seguinte trecho:

```yaml
spec:
  containers:
  - image: nginx
    name: meu-pod
    env:
    - name: NGINX_PORT
      value: "80"
    ports:
    - containerPort: 80
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
```

E criar o pod através do comando:

```bash
kubectl create -f meu-pod.yaml
```

</details>