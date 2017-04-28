# **Guia de configuração do dcrd**

Última atualização para a v0.8.2.

Este guia tem por objetivo, auxiliar você a configurar o software `dcrd` utilizando [startup flags](/getting-started/startup-basics.md#startup-command-flags). 

**Pré-requisitos:**

- Utilize a última versão do [dcrinstall](/getting-started/install-guide.md#dcrinstall) para instalar o `dcrd`. Algumas etapas adicionais serão necessárias caso você tenha utilizado outro método de instalação.
- Reveja como os de inicialização dos shells Prompt de Comando (Windows) e Bash (OSX/Linux) se diferenciam [aqui](/getting-started/cli-differences.md).

---

`dcrd` é o node daemon da Decred. Daemon é um programa que funciona em segundo plano, e que você não interage diretamente com ele. O `dcrd` mantém o registro de todas as transações que ocorreram (ou blockchain) da Decred e permite a retransmissão das transações para outros nodes da Decred no mundo. Você pode considerá-lo como sendo o seu próprio servidor da blockchain da Decred. A blockchain é salva na pasta `data` dentro do diretório `dcrd`.

**Usuários avançados: Se você estiver rodando em headless mode via SSH,** você terá que 
utilizar um terminal multiplexer tal como o [screen](http://www.howtogeek.com/howto/ubuntu/keep-your-ssh-session-running-when-you-disconnect/)
ou o [tmux](https://tmux.github.io/). Quando você ver a instrução para
mudar para outra shell, você terá que iniciar uma nova janela no `screen`
ou no `tmux`.

---

## **<i class="fa fa-cloud"></i> Conecte-se à rede da Decred**

A primeira vez que inicializar o `dcrd`, irá conectá-lo à rede da Decred e iniciar o download da blockchain. Para permitir que a `dcrwallet` e o `dcrctl` se comuniquem com o `dcrd`, os arquivos de configuração deverão ter as definições de `rpcuser` e `rpcpass` habilitadas. 

> Configurando o Username e Password do RPC

Se você utilizou o [`dcrinstall`](/getting-started/install-guide.md#dcrinstall), seus arquivos de configuração já estão configurados com o Username e Password do RPC username/password para o `dcrd`, a `dcrwallet`, e o `dcrctl`.

Se você não utilizou o `dcrinstall`, você terá que habilitar as configurações mínimas nos arquivos de configuração. Para isso, siga [este guia](/getting-started/startup-basics.md#minimum-configuration).

> Inicie o dcrd 

Com as definições corretas nos arquivos de configuração, abra uma outra janela da shell, na sua pasta Decred (ou utilize a última janela, caso tenha recém criado sua carteira). Digite os seguintes comandos (reveja os pré-requisitos deste guia, para determinar qual o comando correto a se utilizar, a depender do sistema operacional ou shell que estiver utilizando):

```no-highlight
dcrd
```

> Aguarde o dcrd sincronizar com a Blockchain Decred

Quando o `dcrd` inicia corretamente, você deverá ver a janela da shell sendo preenchida com mensagens ao passo que o daemon se conecta com a rede e inicia o processamento dos blocos. Aguarde até que seja finalizado - toda a blockchain está sendo baixada para a pasta `dcrd`. 

Você verá uma linha que começa assim:

```no-highlight
22:58:04 2016-02-09 [INF] BMGR: Syncing to block height 617 from peer 104.236.167.133:9108
```

Depois, enquanto continua fazendo o download dos blocos, você verá algumas linhas assim:

```no-highlight
22:58:16 2016-02-09 [INF] BMGR: Processed 321 blocks in the last 10.03s (544 transactions, height 322, 2016-02-09 09:50:34 +1000 EST)
```

A blockchain estará completamente sincronizada quando o último bloco processado, coincidir com a altura do bloco atual. Você poderá confirmar isso de duas formas, comparando a data e horário na mensagem do log ou comparando a altura do último bloco processado com a altura do último bloco processado no [explorador de blocos oficial](https://mainnet.decred.org/).  

Note que esta conexão será utilizada no futuro. Você deverá deixar a instância `dcrd` sendo executada, para utilizar a `dcrwallet`.

---

Agora que já já configurou o `dcrd`, visite o guia de configuração da [dcrwallet](/getting-started/user-guides/dcrwallet-setup.md) guide.