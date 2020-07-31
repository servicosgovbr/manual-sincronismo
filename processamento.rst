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

Extrutura do JSON
+++++++++++++++++

.. code-block:: json
    
    {
      "id": 0,
      "form_versao": "<VALOR PREENCHIDO>",
      "IDE_FINALIZADO": "<VALOR PREENCHIDO>",
      "DES_TITULO": "<VALOR PREENCHIDO>",
      "metadados": [
        {
          "COD_PROCESSO_F": 0,
          "COD_ETAPA_F": 0,
          "COD_CICLO_F": 0,
          "CPF": "<VALOR PREENCHIDO>",
          "PROTOCOLO": "<VALOR PREENCHIDO>",
          "<DADOS DO FORMULARIO>": "....",
	      "TITULO_ETAPA": "<VALOR PREENCHIDO>",
	      "PROCESSOS_ETAPAS": {
                  "COD_CICLO": 0,
                  "COD_ETAPA": 0,
                  "APROVACAO_MOB": "<VALOR PREENCHIDO>",
                  "COD_USUARIO_ETAPA": 0,
                  "DAT_FINALIZACAO": "<VALOR PREENCHIDO>",
                  "DAT_GRAVACAO": "<VALOR PREENCHIDO>",
                  "IDE_STATUS": "<VALOR PREENCHIDO>",
                  "IDE_STATUS_ANT": "<VALOR PREENCHIDO>",
                  "IDE_TEMPORARIO": "<VALOR PREENCHIDO>",
                  "IDE_VISUALIZADO": "<VALOR PREENCHIDO>",
                  "NOM_ARQ_ASSINADO": "<VALOR PREENCHIDO>",
                  "uuid": "<VALOR PREENCHIDO>",
                  "VLR_ATRASO1": 0,
                  "VLR_CAMPOS_COMPLEM": "<VALOR PREENCHIDO>",
                  "VLR_QTDE_ALERTA": 0,
                  "VLR_QTDE_ATRASO": 0,
                  "VLR_TEMP_ATR_GEST": 0,
                  "VLR_TEMP_HIBERNA": 0,
                  "VLR_TEMP_LIM_GEST": 0,
                  "VLR_TEMPO_ALERTA": 0,
                  "VLR_TEMPO_ATRASO": 0,
                  "VLR_TEMPO_CONSUMIDO": 0,
                  "VLR_TEMPO_CONSUMIDO_CORRIDO": 0,
                  "VLR_TEMPO_ESCALONA": 0,
                  "COD_PROCESSO": 0,
                  "DATA_PRINT": 0
               }
	    }
      ],
      "NOME_DA_GRID": [
        {
          "identificador": 0,
          "COD_PROCESSO": 0,
          "COD_ETAPA": 0,
          "COD_CICLO": 0,
          "INDICE": 0,      
	  "<DADOS DA GRID DO FORMULARIO>": "....",
	  "TITULO_ETAPA": "<VALOR PREENCHIDO>"
	}
     ],
     "NOME_DE_OUTRA_GRID": [
        {
          "identificador": 0,
          "COD_PROCESSO": 0,
          "COD_ETAPA": 0,
          "COD_CICLO": 0,
          "INDICE": 0,        
	  "<DADOS DA GRID DO FORMULARIO>": "....",
	  "TITULO_ETAPA": "<VALOR PREENCHIDO>"
	}
        ]
    }

.. note::
    Cada JSON tem dados específicos pois é referente a um serviço único. Verifique com o gestor
    do serviço quais são os campos dos formulários das etapas/ciclos.

Os nomes dos campos estão separados pelo caractere "|". 

No formato: <NOME_DO_CAMPO_NO_FORMULARIO>|<LABEL_DO_CAMPO_NO_FORMULARIO_SE_EXISTIR> ou só o <NOME_DO_CAMPO_DO_FORMULARIO>
