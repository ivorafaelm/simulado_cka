### Questão 10

Qual a quantidade de nodes que estão aceitando novos containers

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

O jeito mais fácil é inspecionar a saída do comando "kubectl describe nodes" e verificar a quantidade de nodes que contêm taints que impedem a execução de pods.

</details>