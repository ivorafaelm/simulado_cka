### Questão 21

Criar Pod com o parametro containerport.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Foi efetuada a criação do arquivo meu-pod.yaml.
O arquivo está versionado para facilitar o entendimento.

Abaixo segue a transcrição do arquivo meu-pod.yaml:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-nginx
spec:
  selector:
    matchLabels:
      run: my-nginx
  replicas: 2
  template:
    metadata:
      labels:
        run: my-nginx
    spec:
      containers:
      - name: my-nginx
        image: nginx
        ports:
        - containerPort: 80
```


</details>