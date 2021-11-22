### Questão 13

Realizar o backup do etcd.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para efetuar o backup do ETCD nós precisamos levantar as informações referentes ao caminho da chave, CA e certificado utilizados pela solução. Para isso é necessário efetuar a localização destes caminhos em um nó master (em uma instalação tradicional é neste tipo de nó que o ETCD estará presente - atentar aos casos em que o ETCD é instalado em máquinas exclusivas).

Estes caminhos podem ser obtidos através dos caminhos abaixo (por padrão):

```bash
# Um dos nodes onde o ETCD está em execução.
cd /etc/kubernetes/manifests
cat etcd.yaml
grep etcd kube-apiserver.yaml
```

Após o levantamento dos caminhos é necessário efetuar o backup através do utilitário etcdctl (que pode não estar presente nos nós, sendo necessária a sua prévia instalação).

```bash
# Com essas informaçoes, já podemos criar o nosso snapshot
ETCDCTL_API=3 etcdctl snapshot save snap_do_gerente.db --key /etc/kubernetes/pki/apiserver-etcd-client.key --cacert /etc/kubernetes/pki/etcd/ca.crt --cert /etc/kubernetes/pki/apiserver-etcd-client.crt
```

</details>