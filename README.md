# Network Log Analyzer
O sistema é responsável por ler arquivos log de redes. Entre ele, registros como tentativas de conexão, falhas de autenticação ou acesso bloqueados, processar informações, identificar eventos críticos e salvar um resumo filtrado em um novo arquivo. O objetivo é que cada etapa tenha um filtro independente: um filtro lê os dados, outro irá extrair apenas informações relevantes, outro analisa incidentes graves, e outro salva o resultado final.

A aplicação possui quatro filtros principais:

* FiltroLeituraLogs
* FiltroExtracaoEventos
* FiltroClassificacaoDeEventos
* FiltroEscreveRelatorio

FiltroLeituraLogs - Recebe o arquivo, faz a leitura de cada linha de registro de logs de rede e depois envia para exfiltração.

FiltroExtracaoEventos - Recebe as linhas e busca por termos recorrentes como failed, success, etc. Esses termos irão auxiliar para os eventos possam ser classificados e enviados para o módulo de classificação.

FiltroClassificaçãoDeEventos - Recebe os dados enviados pela função de extração e classifica de acordo com o termo exfiltrado envia para função que irá gerar relatório.

FiltroEscreveRelatorio - Recebe os dados tratados e gera um arquivo com informações.
