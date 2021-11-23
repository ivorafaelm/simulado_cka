### Questão 16

Adicionar mais um node no cluster.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para adicionar um nó ao cluster (caso ele tenha sido criado através do kubeadm) nós devemos utilizar o seguinte comando:

```bash
kubeadm join --token <token> <control-plane-host>:<control-plane-port> --discovery-token-ca-cert-hash sha256:<hash>

```

Estas informações são apresentadas no momento da inicialização do cluster, assim o ingresso dos demais nós no momento da criação é bem tranquilo, pois basta copiar o comando e colar nas demais máquinas.

Caso esse ingresso seja em momento posterior, será necessário obtermos novos tokens, conforme segue abaixo:

```bash
# Para obetermos o token a ser utilizado no join
kubeadm token create
# A saída será algo como:
5didvk.d09sbcov8ph2amjw

# Para obetermos o valor a ser utilizado como parâmetro do --discovery-token-ca-cert-hash
openssl x509 -pubkey -in /etc/kubernetes/pki/ca.crt | openssl rsa -pubin -outform der 2>/dev/null | \
   openssl dgst -sha256 -hex | sed 's/^.* //'
# A saída será algo como:
8cb2de97839780a412b93877f8507ad6c94f73add17d5d7058e91741c9d5ec78

# O comando final teria a seguinte forma:
kubeadm join --token 5didvk.d09sbcov8ph2amjw <control-plane-host>:<control-plane-port> --discovery-token-ca-cert-hash sha256:8cb2de97839780a412b93877f8507ad6c94f73add17d5d7058e91741c9d5ec78
```

</details>