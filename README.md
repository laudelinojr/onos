# Instalação do ONOS - Open Network Operating System  :cloud:

### XXXx
[ONOS](https://***)

## Requisitos mínimos de hardware
- 2 processadores
- 8 Gb de RAM
- 60 Gb disco

## Sistema Operacional
- Ubuntu18.04 (64-bit variant required)

## Passo a Passo para instalação

1) Instalar o Sistema Operacional, conforme requisitos de hardware já citados, no mínimo.

Obs1.: O usuário default do Ubuntu pode ser o "sdn", que será utilizado mais a frente.

Obs2: A execucção conforme observação 1 evitará que seja necessário criar um novo usuário e digite o comando:
sudo adduser sdn --system --group

2) Criar diretório /opt caso nao exista
```bash
sudo mkdir /opt
cd /opt
```

3) Baixar projeto no site do ONOS
```bash
sudo wget -c https://repo1.maven.org/maven2/org/onosproject/onos-releases/2.5.1/onos-2.5.1.tar.gz
```

4) Descompactar
```bash
sudo tar xzf onos-2.5.1.tar.gz
```
5) Renomear diretorio
```bash
sudo mv onos-2.5.1 onos
```

5) Configurar para ser por serviço.
```bash
sudo cp /opt/onos/init/onos.initd /etc/init.d/onos
sudo cp /opt/onos/init/onos.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable onos
 ```
 
 Execute o comando
```bash
sudo tee /opt/onos/options <<-'EOF'
ONOS_USER=sdn
# Optional: add any apps here that you wish to activate by default
ONOS_APPS=
EOF
```
6) Confirme se o arquivo foi criado
```bash
cat /opt/onos/options
```

7) Comando para iniciar o serviço
sudo systemctl start onos.service
Obs.: Após configurações já descritas, este serviço será iniciado automaticamente.

8) Instalando mais uma dependencia
sudo apt-get install curl


Links:

http://fhs.pro.br/?page_id=2785

https://www.youtube.com/watch?time_continue=2010&v=s2hTj0gMre8&feature=emb_logo

https://opennetworking.org/onos/

https://wiki.onosproject.org/display/ONOS/User's+Guide

https://wiki.onosproject.org/display/ONOS/

https://wiki.onosproject.org/display/ONOS/Requirements

https://wiki.onosproject.org/display/ONOS/Running+ONOS+as+a+service

https://wiki.onosproject.org/display/ONOS/Managing+ONOS+applications
