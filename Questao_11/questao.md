### Questão 11

Criar um secret e dois pods, um montando o secret em filesystem e outro como variável.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para criar o secret podemos efetuar a seguinte sequência de comandos:

```bash
kubectl create secret generic my-secret --from-literal user=usuario --from-literal password=senhasecreta
```

Para a criação dos pods nós podemos executar a seguinte sequência de comandos:

```bash
kubectl create -f pod-secret-env.yaml
kubectl create -f pod-secret-file.yaml
```

</details>