Processamento dos arquivos
==========================

Você pode processar os arquivos da forma que desejar.

Uma forma é utilizar o inotify API ou inotify-tools para 
processar quando um arquivo for escrito.

Exemplo simples de processamento
++++++++++++++++++++++++++++++++

.. code-block:: bash
   :emphasize-lines: 2
   :caption: Espera o evento de modificação e processa o arquivo. Leitura não dispara o processo.
    
    #!/bin/sh
    while inotifywait -e modify /meu/arquivo/json; do
        if tail -n1 /meu/arquivo/json | grep id=33; then
            /meu/processamento/processa.py /meu/arquivo/json
        fi
    done


Veja o manual do inotify-tools:
https://linux.die.net/man/1/inotifywait

Wiki do inotify-tools:
https://github.com/inotify-tools/inotify-tools/wiki

.. note::
    Cada JSON tem dados específicos pois é referente a um serviço único. Verifique com o gestor
    do serviço quais são os campos dos formulários das etapas/ciclos.
