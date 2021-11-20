### Questão 08

Ver quais os pods que mais estão consumindo cpu através do kubectl top.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

```bash
kubectl top pod
```

Podemos utilizar outras formas, tais como:

```bash
kubectl top pod POD_NAME --containers
kubectl top pod POD_NAME --sort-by=cpu
```

</details>