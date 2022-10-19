# jenkins
<h1>Implantação Jenkins</h1>

> Status: Produção

Para que o Jenkins é usado?
Jenkins é usado para construir e testar o seu produto continuamente, para que os desenvolvedores possam integrar continuamente as mudanças na construção. Jenkins é a ferramenta de CI / CD de código aberto mais popular no mercado hoje e é usado no suporte de DevOps, junto com outras ferramentas nativas da nuvem.

Automação, incluindo CI / CD e automação de teste, é uma das principais práticas que permitem que as equipes de DevOps entreguem soluções de tecnologia “mais rápidas, melhores e mais baratas”.

Portanto, Jenkins se tornou uma ferramenta indispensável para ajudá-lo a atingir esses objetivos. Jenkins tem sido uma tecnologia de capacitação chave que está ajudando cada vez mais as práticas de DevOps a serem amplamente adotadas em muitas organizações em todo o mundo.

1. INSTALAÇÃO JENKINS KUBERNETES

 - Nos arquivos .yaml nesse repositório você será capaz de subir o Jenkins de modo persistente.
 -  Execute primeiro a criação do namespace "namespace_jenkins" depois o restante dos .yaml
    kubectl apply -f namespace_jenkins
 - Validar como o seu cluster esta configurado o StorageClass, nessa implantação estava configurado um NFS.
