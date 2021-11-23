### Questão 15

Usar o nslookup e/ou outras ferramentas para pegar o dns do pod e do service.

<details> 
  <summary><b>Resposta</b> <em>(clique para ver a resposta)</em></summary>

Para conseguirmos exemplificar a resolução de DNS é possível efetuar a criação de um pod genérico (p.ex um com a imagem do nginx) e seguir os seguintes passos:
1º - Efetuar a criação do pod e de um service

```bash
kubectl run meu-pod --image nginx --port 80 --dry-run=client -o yaml > meu-pod.yaml
kubectl create -f meu-pod.yaml
kubectl expose pod meu-pod --type NodePort
```

```bash
# Efetuar o acesso direto ao shell do container do pod
kubectl exec meu-pod -it -- bash
# Caso o utilitário nslookup não esteja presente é necessário efetuar a sua instalação
apt update
apt install dnsutils
# Verificar as entradas criadas no arquivo /etc/resolv.conf
nameserver 10.96.0.10
search default.svc.cluster.local svc.cluster.local cluster.local
options ndots:5
# Verificar as entradas criadas em /etc/hosts
127.0.0.1	localhost
::1	localhost ip6-localhost ip6-loopback
fe00::0	ip6-localnet
fe00::0	ip6-mcastprefix
fe00::1	ip6-allnodes
fe00::2	ip6-allrouters
10.1.0.46	meu-pod
# Testar a resolução do nome do serviço criado anteriormente
nslookup meu-pod
# A saída deve ser algo como:
Server:		10.96.0.10
Address:	10.96.0.10#53

Name:	meu-pod.default.svc.cluster.local
Address: 10.107.108.62

```

</details>