### Questão 27

Criar um volume Emptydir e compartilhar entre 2 containers.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para efetuar a configuração de um EmptyDir e compartilhar entre dois containers nós podemos utilizar o arquivo meu-pod.yaml abaixo:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: meu-pod
spec:
  containers:
  - image: nginx
    name: nginx-container-01
    volumeMounts:
    - mountPath: /mnt/cache
      name: cache-volume
  - image: busybox
    name: nginx-container-02
    volumeMounts:
    - mountPath: /mnt/cache
      name: cache-volume
  volumes:
  - name: cache-volume
    emptyDir: {}
```

E criar o pod através do comando:

```bash
kubectl create -f meu-deployment.yaml
```

No exemplo acima o pod vai apresentar falha no livenessProbe após 30 segundos, uma vez que o arquivo que a ser aberto já não existirá mais, fazendo com que o pod seja restartado.

</details>