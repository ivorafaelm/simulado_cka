### Questão 20

Criar um cronjob.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Foi efetuada a criação do arquivo meu-cronjob.yaml.
O arquivo está versionado para facilitar o entendimento.

Os principais pontos do arquivo são os trechos referentes ao agendamento e a execução dos comandos no container. 

Abaixo segue a transcrição do arquivo meu-cronjob.yaml

```yaml
apiVersion: batch/v1
kind: CronJob
metadata:
  name: hello
spec:
  schedule: "*/1 * * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: hello
            image: busybox
            imagePullPolicy: IfNotPresent
            command:
            - /bin/sh
            - -c
            - date; echo Hello from the Kubernetes cluster
          restartPolicy: OnFailure
```


</details>