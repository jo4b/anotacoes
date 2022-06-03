# Anotações 25/04/2022
### Programa da disciplina, WSL windows, advanced port sccaner, etckeeper

---------------

### Programa da disciplina:

* Instalar distro do linux para servidor ou contêines.
* Configuração de interfaces de rede.
* Instalação, configuração, uso e teste de serviços:
  * Servidor web (HTTP).
  * Servidor proxy e proxy reverso.
  * Servidor de registros (LOG).
  * Servidor de banco de dados.
  * Servidor de arquivos (FTP).
  * Servidor de autenticação.
  * Servidor de nomes e dominio (DNS).
  * Servidor de acesso remoto (SSH).
  * Servidor de contêines.
  * Servidor de configuração de dinâmica de hosts.
-----------  
### Alunguns programas intalados em aula no Windows:

1. WSL - Ubuntu, disponivel na loja microsoft.
2. Servidor apache.
3. Advanced port scanner.
-----------------
### Comando que julguei interesssante

Listar diretórios no powershell, semelhante ao comando do linux `ls`
```markdown
pwsh: dir
```
-----------


# Anotaçẽos 02/05/22 e 09/05/22
### IP, interface de rede, par de chaves, vscode extensions, etckeeper comandos
----------------

### Alguns comandos aprendidos:

Listar interfaces de rede:
`ip -c -br link`
Filtra endereço ipv4 da máquina:
`ip -c -br -4 addr`

```mermaid
graph 
c --> cor
br --> abreviar
link --> interfaces
```
-----
Mostra endereço ip da máquina: 
`hostname -I`

Mudar o shell:
`chsh`
> Lembrar de especificar o shell que quer usar /bin/shell*

Lista todo conteudo do diretório atual inclusive os arquivos ocultos e enumera em uma lista:
`ls -FA1 | nl`

Executa o ultimo argumento passado:
`source $_`

-------
### Algumas extensões instaladas no VSCODE

```markdown
1. vscode icons.
2. markdown all in one.
3. markdown preview.
4. docs-markdown.

```
 -------

### Aplicações instaladas no linux

`ETCKEEPER + comandos`:

```mermaid
graph

etckeeper --> log & status & diff & checout

```
---------------------

`pip3`

---------------------


# Semana 17/05/2022 e 24/05/2022
### Alterar nome da maquina, interface de rede, ssh, contêines
> Assunto: Nome da maquina, interface de redem e SSH (cliente e servidor)

**Chaves públicas e privadas (keygen)**
[Github](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
```markdown
ssh-keygen (id, id.pub)
ssh-copy-id USER@SERVER
```
------------
### Semana 24/05/2022

**Assuntos:** LXD/LXC, servidor ssh e serviços,
LXD: Daemon,
LXC: Cliente e comando


**Para checar os grupos ao qual seu usuário esta inserido:**
`$ groups USER` ou por exemplo `$ getent groups lxd` para obter informações de forma mais simples e objetiva. Use `newgrp` para aplicar as mudanças de grupo sem precisar fazer logoff.

**Comandos de gerenciamento e criação de conteines lxc/lxd**
```markdown
$: lxc list --help
$: lxc -c n4s
$: lxc launch images:ubuntu/22.04 NOME
$: lxc launch images:debian/11 NOME
$: lxc list images: | grep DISTRO
$: lxc launch images:alpinme/edge NOME
```

**Portas abertas do TCP**
```markdown
$: ss -tl
$: ss -tnl
```
**Portas abertas do UDP**
```markdown
$: ss ul
$: ss unl
```
**Configuração de interfaces de rede DEBIAN/ALPINE**
```markdown
$: /etc/network/interfaces
$: ifdown INTERFACE
$: ifup INTERFACE
```

**Configuração de interfaces UBUNTU/UBUNTU-SERVER**
```markdown
$: /etc/netplan/*yaml
$: netplan try
ou $ netplan apply
```

**Verificar informações sobre um pacote**
```markdown
$: apt show PACOTE
```
**Comandos para hora e data**
```markdown
$: date
$: timedatectl
```
**Aplicação para comparar arquivos**
```markdown
$: meld ARQUIVO-X ARQUIVO-Y
```

**Listar todas as portas TCP/UDP**
```markdown
$: sudo netstat -tulnp
```

**Instalar o code-server**
[Link para instalar](https://github.com/coder/code-server)

# Gerar um par de chaves ssh
1 - Gerar uma nova chave SSH
Abra Terminal.

2 - Cole o texto abaixo:
```markdown

$ ssh-keygen -t ed25519 
```
### Adicionar sua chave SSH ao ssh-agent
Antes de adicionar uma nova chave SSH ao agente para gerenciar suas chaves, você deve verificar as chaves SSH existentes e gerado uma nova chave SSH.
Inicie o ssh-agent em segundo plano.
```mardown
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```
Adicione sua chave SSH privada ao **ssh-agent**. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.
```markdown
$ ssh-add ~/.ssh/id_ed25519
```
### Adicionar sua chave privado ao serviço ssh
```markdown
$ ssh-copy-id SERVIÇO
```

# Configuração interface de rede com netplan
1 - Exemplo de uma configuração dinâmica.
```yaml
network:
   version: 2
   renderer: NetworkManager
   ethernets:
      enp0s3:
        dhcp4: yes #or true
      enp0s8: 
        dhcp4: yes #or true

```
2 - Exemplo de uma configuração estática.
```yml
network:
   version: 2
   renderer: NetworkManager
   ethernets:
      enp0s3:
        dhcp4: no #or false
        addresses: [192.168.1.10/24] #ip e mask
        nameservers: # dns
            addresses: [8.8.8.8, 8.8.4.4]
        routes: #novo metodo pra gateway
            - to: default
              via: 192.168.1.1 #gateway da rede
```
-----------------------------------
# Semana 01/06/2022
--------------------------------
### asciinema, ssh e http
-------------------------------------
**asciinema**:
> asciinema é um software capaz de gravar os comandos digitados no terminal, para analise/estudo futuros. 
> As gravações ficam salvas por 7 dias, podendo ficar para "sempre" salva no site oficial, fica a criterio do usuário.

1 - Para saber todos os comandos asciinema
```markdown
$ asciinema rec --help
```
2 - Para gravar tela do shell.
```markdown
$ asciinema rec -i 2.5 -t "TITULO"
```
-------------------------------
### Instalação de servidores ssh e http

1 - Servidor de acesso remoto(ssh)
```markdown
$ sudo apt update -y
$ sudo apt install openssh-server -y
```
2 - Servidor web (http) - lighttpd e apache2
```markdown
$ sudo apt update -y
$ sudo apt install apache2 -y
$ sudo apt install lighttpd -y
```