### Questão 23

Declarar a variável na configmap e passar para container.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para efetuar a configuração de um configmap nós podemos usar o seguinte comando:

```bash
kubectl create configmap credenciais --from-literal=user=usuario_secreto --from-literal=password=senha_secreta
```

Para criar o pod com os valores do configmap como variável de ambiente podemos usar o seguinte yaml:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-configmap
  namespace: default
spec:
  containers:
  - image: nginx
    name: nginx-configmap
    env:
    - name: frutas
      valueFrom:
        configMapKeyRef:
          name: cores-frutas
          key: predileta
```

E criar o pod através do comando:

```bash
kubectl create -f meu-pod.yaml
```

</details>