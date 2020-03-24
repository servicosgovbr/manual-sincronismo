Passos para receber os arquivos JSON
====================================

* Servidor ssh/rsync;
* Liberar acesso do IP;
* Enviar configurações;
* Adicionar chave pública;

Servidor ssh/rsync
++++++++++++++++++

É necessário um servidor com o ssh habilitado e o rsync instalado.

Geralmente o rsync já vem instalado nas distribuições do Linux, 
mas se for necessário instalar as instruções verifique a forma de instalar no seu sistema.
O manual online do rsync se encontra em https://linux.die.net/man/1/rsync

Liberar acesso do IP
++++++++++++++++++++

O IP que iremos utilizar como saída das informações é 18.228.115.216.


Enviar configurações
++++++++++++++++++++

Ao mesmo tempo, precisamos saber qual é o endereço do servidor de vocês e o número da porta que será aberta para a conexão SSH.
Além disso, a pasta que iremos gravar o arquivo e o usuário que vai receber. 
O usuário precisa de permissão de escrita na pasta. 


Adicionar chave pública
+++++++++++++++++++++++

Ao enviar as configurações iremos enviar para você a chave pública para acesso automatizado.
Ver o passo 3 do guia como instalar https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2

.. attention::
   O arquivo vai ser sempre adicionado da diferença. Caso deseje ter um histórico é necessário copiar o arquivo diariamente para outro local.
