### Questão 26

Configurar liveness e readiness no deployment.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para efetuar a configuração de liveness e readiness probes nós podemos incluir as seções livenessProbe e readinessProbe no yaml, conforme exemplificado no arquivo meu-deployment.yaml (descrito abaixo):

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: meu-deployment
  name: meu-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: meu-deployment
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: meu-deployment
    spec:
      containers:
      - image: nginx
        name: nginx
        ports:
        - containerPort: 80
        args:
        - /bin/sh
        - -c
        - touch /tmp/healthy; sleep 30; rm -rf /tmp/healthy; sleep 600
        livenessProbe:
          exec:
            command:
            - cat
            - /tmp/healthy
          initialDelaySeconds: 5
          periodSeconds: 5
        readinessProbe:
          exec:
            command:
            - cat
            - /tmp/healthy
          initialDelaySeconds: 5
          periodSeconds: 5
        resources: {}
status: {}
```

E criar o pod através do comando:

```bash
kubectl create -f meu-deployment.yaml
```

No exemplo acima o pod vai apresentar falha no livenessProbe após 30 segundos, uma vez que o arquivo que a ser aberto já não existirá mais, fazendo com que o pod seja restartado.

</details>