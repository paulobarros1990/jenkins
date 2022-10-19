![moodle1](https://user-images.githubusercontent.com/114024164/196735400-be7d8bbd-255c-4ab6-9fcb-320a043709c2.jpg)

> Status: Produção

### Descrição Executiva

Esse documento apresenta projeto de inovação tecnológica, em consonância com os itens XI.02, XI.03 e XI.17, objeto do contrato 05/2021 – Processo Nº 47648.000354/2020-64, com o objetivo de propor a implantação da Plataforma Moodle na infraestrutura da Fundacentro.

### Descrição Técnica

O projeto consiste na criação de um ambiente da plataforma Moodle. O Moodle é uma plataforma de aprendizagem projetada para fornecer a educadores, administradores e alunos um único sistema robusto, seguro e integrado para criar ambientes de aprendizagem personalizados.

## Tecnologias Usadas
<table>
  <tr>
     <td>Docker</td>
	 <td>Compose</td>
  <td>Nginx</td>
    <td>Moodle</td>
	  <td>MariaDb</td>
  </tr>
  <tr>
     <td>1.13</td>
	 <td>1.29</td>
   <td>1.20</td>   
   <td>4.0</td>
   <td>10.6</td>
  </tr>	 
</table>

## Topologia
![infra_moodle](https://user-images.githubusercontent.com/114024164/196743875-42f83b85-34cb-4348-8abe-eb0e6f6f5fa0.png)

## Instalação
+ yum install docker -y
+ systemctl enable docker
+ systemctl start docker
+ curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

## Docker Compose
Apos instalação dos serviços necessários escrever o manifest no arquivo docker-compose.yaml.
> docker-compose.yaml

![compose](https://user-images.githubusercontent.com/114024164/196747558-6f0aab6a-53da-41f7-bcbf-239a07a3a474.JPG)

## Executando o docker-compose.yaml
+ cd /opt/docker-moodle
+ docker-compose up -d

![compose1](https://user-images.githubusercontent.com/114024164/196748771-52cda449-0e30-43a0-97ff-d1122c609a5a.JPG)

## Nginx
vim  /etc/nginx/sites-available/ead.fundacentro.gov.br.conf
> Configuração do arquivo Nginx

![nginx](https://user-images.githubusercontent.com/114024164/196750680-bc238137-3fd0-494b-b94a-37c242c92fdd.JPG)

## Certificado
O certificado utilizado é da https://letsencrypt.org/pt-br/, quando gerado o certificado tem validade de 90 dias, foi criado um agendamento para renovar o certificado de forma automática quando estiver faltando 30 dias para vencer.

> Renovação Certificado

![certificado](https://user-images.githubusercontent.com/114024164/196755028-cff801f0-815e-4bb6-b03c-b6df26b302a6.JPG)

## Scripts
Foram criados 3 scripts para automatizar algumas tarefas.
* /opt/scripts/backup_moodle.sh

![script_backup](https://user-images.githubusercontent.com/114024164/196757390-5feddcba-0490-4412-b1e4-8c2413cf6ebf.JPG)

* /opt/scripts/expurgo_backup_moodle.sh

![script_expurgo_backup](https://user-images.githubusercontent.com/114024164/196757670-866d9780-0b6d-4af7-9a6b-5109c42a6a3d.JPG)

* /opt/scripts/start_moodle.sh

![script_start_moodle](https://user-images.githubusercontent.com/114024164/196757910-549d579e-baae-4ad8-be97-149bac1050ed.JPG)

## Backup
Os dados persistentes de configurações do Moodle e do Banco de dados estão sendo gravados no disco local do servido dentro da partição /opt/docker-moodle/, o script backup_moodle.sh faz o backup desse diretório e salva em um diretório NFS que esta montando no servidor.

> NFS

![nfs](https://user-images.githubusercontent.com/114024164/196759154-7e7e7c4c-7eb6-4bcb-9e0b-0af57eac41b9.JPG)

## Monitoramento
Foi criado um monitoramento web e do serviço docker no zabbix





