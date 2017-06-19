MariaDB Server
==============
Ansible Role para instalar servidor MariaDB 10.2 (MySQL Fork) e cadastrar usuários e bancos de dados.

Usuários devem ser cadastrados no playbook que executa este role. Este role não remove usuários ou os bancos de dados, apenas inclui.

Requisitos
----------
CentOS 7

Variaveis do Role
-----------------
O bloco de variavel _user_ contem as variaveis necessarias para criação dos usuários:

Nome do usuário:
```yaml
username: joe
```

Senha do usuário:
```yaml
password: joeLongPassword
```

Banco de dados:
```yaml
database: joe
```

Hosts autorizados:
```yaml
allowed_host: 192.168.0.20
```
Obs: Se utilizar o simbolo '%', todos os hosts de origem serão autorizados.

Dependências
------------

Nenhuma.

Playbook de exemplo
-------------------
```yaml
---
- name: Instala MariaDB  Server 10
  hosts: all
  become: true
  gather_facts: true
          
  roles:
    - role: mariadb_server
      users:
        - username: alice
          password: aliceLongPassword
          database: alice
          allowed_host: "%"
  
        - username: bob
          password: bobEvenLongerPassword
          database: bob
          allowed_host: 192.168.64.1

```

TODO
-------
- Suporte a SSL/TLS para comunicação entre cliente e servidor.

Licença
-------

MIT

Informações do Autor
--------------------

Fabricio Boreli  
fabricioboreli@openmailbox.org
