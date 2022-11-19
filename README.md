# CoD Watcher
Um bot Discord para servidores Call of Duty 1. Os recursos incluem status do servidor ao vivo, logs de bate-papo, alertas de relatório e banimento e automute de spam e palavrões.

## Setup

### Gameserver
Os arquivos referentes ao seu servidor CoD estão na pasta "servidor". Abra.

1. Adicione `codwatcher.log` e `codwatcher.cfg` à pasta "principal" (ou fs_game) do seu servidor.
2. Inclua `codwatcher.cfg` em seu arquivo de configuração do servidor com extensão`exec codwatcher.cfg`.
3. Adicione `codwatcher.gsc` à pasta "codam" do seu servidor.
4. Adicione o mod ao CoDaM "modlist.gsc" -  `[[ register ]]( "CoD Watcher", codam\codwatcher::main );`.

Para usar o plugin com MiscMod, faça o seguinte:

1. Abra  "codam/_mm_commands.gsc"
2. Procurar por `str = codam\_mm_mmm::strip(str);`
3. Adicione o seguinte código acima dessa linha:
    ```c
        if(!self codam\codwatcher::message(str)) {
            creturn();
            return;
        }
    ```

Para usar o plug-in com outros sistemas de comando de bate-papo, adicione o mesmo bloco de código do MiscMod em sua função de retorno de chamada de mensagem de bate-papo. Você também precisará incluir sua lógica de ativar/desativar o som no arquivo "codwatcher.gsc".

### Bot

1. Coloque a pasta "bot" em algum lugar no diretório do servidor. Assumiremos que você o colocou fora de sua pasta "principal".
2. Vá para a pasta "bot".
3. Configure as configurações em "config.json".
4. Instale os módulos necessários com `npm install`.
5. Execute o bot com o seguinte comando `node app.js`.
