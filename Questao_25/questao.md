### Questão 25

Configurar resources limits no deployment.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para efetuar a configuração de um secret nós podemos usar o seguinte comando:

```bash
kubectl create secret generic my-secret --from-literal user=usuario_secreto --from-literal password=senha_secreta
```

Para criar o pod com os valores do secret como variável de ambiente podemos usar o seguinte yaml:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: meu-pod
spec:
  containers:
  - name: meu-pod
    image: nginx
    resources:
      requests:
        memory: "256Mi"
        cpu: "250m"
      limits:
        memory: "512Mi"
        cpu: "500m"
```

E criar o pod através do comando:

```bash
kubectl create -f meu-pod.yaml
```

</details>