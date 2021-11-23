### Questão 19

Ajustar o nome de uma imagem com nome errado de um deployment.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para efetuar o ajuste da imagem de um deployment pode se usar o seguinte comando:

```bash
kubectl create deployment meu-deployment --image nginx --port 80 --dry-run=client -o yaml > meu-deployment.yaml
kubectl create -f meu-deployment.yaml
kubectl set image deployment meu-deployment nginx=nginx:1.20
```

Após a execução do comando é possível observar que o arquivo de deployment estará com a nova versão informada:

```bash
kubectl edit deployment meu-deployment
```

O trecho referente a imagem estará com o valor da imagem atualizado, conforme mostrado abaixo:

```yaml
spec:
      containers:
      - image: nginx:1.20
        imagePullPolicy: Always
        name: nginx
```

</details>