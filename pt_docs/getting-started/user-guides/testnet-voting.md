# Guia de Votação para Hard Fork na Testnet (Rede de testes)

Este guia foi atualizado pela última vez para v0.8.2

A partir da versão v0.8.0 lançada em 13 de fevereiro de 2017, o mecanismo de votação hard-fork foi implementado para testes na rede de testes da Decred. A votação teste deverá começar em 25 de fevereiro de 2017 à 1 PM CST e durar 7 dias. Se você deseja participar, os guias para participar utilizando a Paymetheus ou os software de linha de comando podem ser encontrados aqui. 

---

## Introdução

Há um processo de duas fases da votação para implementar mudanças com consenso que criaria um hard fork. Observe: os seguintes intervalos de bloco são para o testnet, eles serão diferentes para o mainnet.

O primeiro passo é atender ao limite de atualização na rede. Depois que o código do hard fork é liberado, a maioria dos nós da rede que participam em mineração PoW/PoS precisa primeiro se atualizar, antes que a votação possa começar. Para a Proof-of-Work, pelo menos 75% dos 100 blocos mais recentes devem ter a versão de bloco mais recente. Para a Proof-of-Stake, 75% dos votos registrados dentro de um intervalo estático de 2016 blocos devem ter a versão de voto mais recente.

O segundo passo deste processo é a votação real. O intervalo anterior de 2016  blocos fica dentro de um intervalo de 5040 blocos maior, e a rede deve aguardar esse intervalo de 5040 blocos maior para terminar. Devido aos diferentes comprimentos de intervalo, isso *pode* levar até 5040 blocos adicionais antes que a janela de votação comece. Depois disso, um intervalo de 5040 blocos ocorre enquanto os votos são feitos e se 75% dos votos minerados dentro desse intervalo, sinalizam um "sim" para as alterações propostas, as mudanças são implementadas completamente após um intervalo de bloco adicional (para dar qualquer nó restante o tempo necessário para atualizar para evitar ser excluído da blockchain). Abaixo, um gráfico simplificado para explicar cada intervalo de blocos na ordem em que aparecem cronologicamente.

Descrição do intervalo | Tipo do Intervalo | Número de Blocos
---------------------|-------------|---------------
Mínimo de 75% dos blocos deverão ser da nova versão | Corrido | 100
Mínimo 75% dos votos deverão ser da nova versão | Estático | 2016
Intervalo após um upgrade ocorre | Estático | Até 5040
Intervalo de votação - 75% dos votos devem sinalizar um "sim" para passar | Estático | 5040
Intervalo de Pré-implementação caso a votação passe | Estático | 5040

Se uma proposta não atingir uma diferença de 10% de votos 'não' ou 'sim', os votantes poderão votar novamente durante o próximo intervalo de votação, até que este limite seja atingido ou a proposta expire.

Abaixo estão instruções para participar da votação demo na Testnet usando uma stakepool com Paymetheus e/ou os softwares de linha de comando `dcrd`,`dcrwallet` e `dcrctl`. O guia de linha de comando usa arquivos de configuração para enviar os parâmetros para o aplicativo durante a inicialização. Como alternativa, as flags podem ser usadas ao iniciar um aplicativo, mas elas não serão incluídas neste rascunho.

## Paymetheus

> Passo 1: Faça o Download e instale a Paymetheus

Se você ainda não atualizou seus binários da Decred para v0.8.2, visite o [Guia de Instalação](/getting-started/install-guide.md) e siga as instruções para o instalador do Windows.

> Passo 2: Execute a Testnet da Decred

No menu Iniciar, abra `Decred Testnet`. Isto irá executar a `Paymetheus`, e uma nova janela de Prompt de Comando será aberta e executando `dcrd.exe`. Se esta é a primeira vez que executa o daemon da testnet, levará algum tempo para sincronizar com a blockchain da testnet.

Na janela `Paymetheus`, aparecerá uma caixa de diálogo "Connect to dcrd". Mantenha os padrões e pressione o botão Continue. A próxima janela terá dois botões, "Create a new wallet" e "Restore wallet from seed". Para este guia, assumiremos que você não tenha uma seed que deseja restaurar.

Depois de clicar em "Create a new wallet", você será recebido com informações sobre a seed de sua carteira. Grave sua seed, coloque-a em um lugar seguro e nunca compartilhe com ninguém. Você também precisará inserir ela assim que pressionar o botão CONTINUAR.

Depois de digitar sua seed, a próxima janela será a Encrypt Wallet. Digite uma senha como as instruções explicam. Pressione ENCRYPT. A Paymetheus então começará a criar sua carteira. Uma vez criado, ele será aberto para sua página de visão geral da carteira.

> Passo 3: Registre ao site da Stakepool

Enquanto aguarda o nó/carteira sincronizar, visite [https://teststakepool.decred.org](https://teststakepool.decred.org) e registre uma nova conta.

> Passo 4: Adquira Decreds da Testnet

Em seguida, você precisará adquirir moedas da Testnet para comprar os tickets. Existe uma Faucet oficial Testnet localizada em [https://faucet.decred.org] (https://faucet.decred.org). Para obter um novo endereço da Paymetheus, clique na guia "Request payment" no menu de navegação. Clique no botão "GENERATE ADDRESS" isso resultará em um endereço que deve começar com "Ts". Copie e cole esse endereço na Faucet e você deverá receber suas moedas.

> Passo 5: Compre Tickets da Testnet

Clique na aba "Purchase tickets" no menu de navegação da Paymetheus. Você verá 7 campos de formulário na página. Todos os padrões podem ser usados para comprar bilhetes **exceto** o "Stake pool preference". Clique no botão "Manage pools". Você precisa inserir a chave da API da sua conta da stakepool da testnet. Para fazer isso, basta visitar [https://teststakepool.decred.org/settings](https://teststakepool.decred.org/settings) - o Token do API deve ser o primeiro item na página. Digite-o no campo API Key na Paymetheus e pressione Salvar. Seu script de 1-of-2 multi-sig será gerado automaticamente e você pode pressionar Fechar.

Em seguida, selecione teststakepool.decred.org na lista suspensa Preference da Stakepool e pressione o botão Comprar para começar a comprar os ingressos! Note: a dificuldade do ticket é igual ao custo por ticket, portanto, certifique-se de ter moedas testnet suficientes para comprar pelo menos um.

> Passo 6: Configure os Votebits dos seus tickets via Stakepool 

Utilizando uma stakepool, qualquer ticket que você compra tem seus direitos de voto delegados a essa stakepool. Por padrão, a pool votará como quiser com seus ingressos. Mas você pode mudar a forma como seus tickets irão votar.

Você pode definir os votos de seus bilhetes através da interface de tickets da stakepool. Abaixo está um print da página [https://teststakepool.decred.org/tickets](https://teststakepool.decred.org/tickets). Na parte inferior da seção "Live/Immature" desta página, você verá as configurações de voto. Você só pode editar os votos de *todos* os seus tickets de uma só vez, através da interface do pool. Os tickets exibidos abaixo foram definidos como "Sim" para "Previous Block Valid?" e "Sim" para "Increase Block Size from 1.0 MiB to 1.25MB" o que resultou em um voto de valor 5. 

<img src="/img/testnet-voting_votebit-setting.jpg">

Para outras informações sobre Votebits, visite [Uma Explicação sobre os Votebits](#an-explanation-of-votebits).

## Instruções de Linha de Comando

> Passo 1: Faça o Download e Instale a Decred

Caso não tenha feito o upgrade do binários da Decred para a versão v0.8.2, visite o [Guia de Instalação](/getting-started/install-guide.md) e siga as instruções para seu ssitema operacional.

> Passo 2: Crie os Arquivos de Configuração (Config Files)

Se você já está familiarizado com os arquivos `.conf`, continue com o Passo 3.

Por favor, veja a nossa [Introdução aos Arquivos de Configuração](/getting-started/startup-basics.md#configuration-files) e crie novos arquivos de configuração ou copie os arquivos de configuração de exemplo nas pastas especificadas para seu sistema operacional.

> Passo 3: Edite os Arquivos de configuração para executar a Testnet

Para executar o `dcrd`, a `dcrwallet` e o `dcrctl` na testnet, basta adicionar `testnet=true` ou `testnet=1` aos três arquivos de configuração. Se você estiver usando um dos arquivos de configuração de exemplo, você pode simplesmente encontrar a linha que lê `;testnet=1` (a primeira configuração na seção Network Settings) e excluir o ponto-e-vírgula.

Isso deve ser feito para os três arquivos de configuração.

> Passo 4: Criar uma nova carteira na Testnet

Se você nunca executou uma carteira na Testnet antes, você precisará criar uma nova. Com a configuração `dcrwallet.conf` para testnet **(ver Passo 3)**, execute `dcrwallet` com a flag `--create`.

Para aqueles que não estão familiarizados com a forma de fazer isso, siga o guia específico do sistema operacional abaixo:

**Windows**: <br />
    1. Utilizando o Prompt de Comando ou o Explorador de Arquivos, navegue até a pasta do executável `dcrwallet` <br />
    2. Se tiver utilizando o Explorador de Arquivos, selecione a opção "Abrir no Prompt de Comando" do menu "Arquivo" <br />
    3. Digite o comando `dcrwallet.exe --create`

**macOS**: <br />
    1. Utilizando o Terminal ou o Finder, navegue até a pasta do executável `dcrwallet` <br />
    2. Se estiver utilizando o Finder, você pode abri um novo Terminal no local da pasta, clicando com o botão direito na pasta e selecionando Services > New Terminal na janela<br />
    3. Digite o comando `./dcrwallet --create`

**Linux**: <br />
    1. Da forma que preferir, navegue até à pasta do executável `dcrwallet` <br />
    2. Digite o comando `./dcrwallet --create`

Isso irá levá-lo ao comando de criar uma nova carteira. Siga as instruções na tela. Você será obrigado a criar uma senha privada (você usará isso mais tarde para desbloquear sua carteira ao criar transações). Uma camada adicional de criptografia é completamente opcional. Sua seed pode ser usada para restaurar sua carteira em qualquer computador usando dcrwallet. Grave sua seed, coloque-a em um lugar seguro e nunca compartilhe com ninguém. A carteira fechará quando tudo estiver terminado.

> Passo 5: Inicie o dcrd na Testnet

Execute o `dcrd` com a opção `testnet = 1` ou `testnet = true` no arquivo de configuração para iniciar o seu node na testnet. Seu node começará a sincronizar com o restante da rede. A sincronização levará um tempo.

> Passo 6: Iniciar dcrwallet na Testnet

Execute a `dcrwallet` com a opção `testnet = 1` ou `testnet = true` no arquivo de configuração para iniciar sua carteira na testnet. Sua carteira se conectará ao seu nó e começará a sincronizar seus endereços. A sincronização pode demorar um pouco.

> Passo 7: Cadastre-se no site da Stakepool

Enquanto espera que seu node/carteira sincronize, visite [https://teststakepool.decred.org](https://teststakepool.decred.org) e registre uma nova conta. Continuar para Passo 8.

> Passo 8: aguarde Testnet Node/Wallet sincronizar

Isso pode demorar um pouco.

> Passo 9: Crie um endereço de Public Key para usar a Stakepool

O primeiro passo para usar uma stakepool é gerar um novo endereço public key a ser usado para gerar um script multisignature 1-of-2. Siga as instruções em [https://teststakepool.decred.org/address](https://teststakepool.decred.org/address) para gerar e salvar este endereço. Se você configurou uma conta em uma stakepool da mainnet, é a mesma coisa.

Passo 10: Importar seu script P2SH Multi-Sig da Stakepool

Em seguida, você precisa importar o script que permitirá que você delegue direitos de voto para a pool. Depois de concluir o [asso anterior, este script deve estar disponível em [https://teststakepool.decred.org/tickets](https://teststakepool.decred.org/tickets). Siga novamente as instruções para importar o script. Se você configurou uma conta em uma stakepool mainnet, isso é a mesma coisa.

> Passo 11: Aquisição de DCR da Testnet

Em seguida, você precisará adquirir moedas da testnet para comprar tickets da Testnet. Existe uma Faucet oficial da Testnet localizada em [https://faucet.decred.org](https://faucet.decred.org). Digite um endereço Testnet (um pode ser gerado executando o comando `getnewaddress` - exemplos para cada OS estão abaixo)

    Windows: dcrctl.exe --wallet getnewaddress
    macOS/Linux: ./dcrctl --wallet getnewaddress

> Passo 12: Compre Tickets da Testnet

[https://teststakepool.decred.org/tickets](https://teststakepool.decred.org/tickets) descreve três opções para comprar tickets. A melhor escolha é usar manual de compra, para que você possa comprar tickets quando precisar.

Rode um comando `dcrctl --wallet getstakeinfo` para ver a dificuldade atual. Este é o preço atual do ticket. Ajuste o comando purchaseticket mostrado na página de tickets da stakepool para considerar o preço atual do bilhete.

> Passo 13: Aguardar o início da votação

Primeiro, um mínimo de 75% de TODOS os votos dos últimos 2016 blocos deve ser de um nó executando o software mais recente da Decred. Em seguida, um intervalo de 5040 blocos deve passar antes do início da votação. Verifique [https://hardforkdemo.decred.org](https://hardforkdemo.decred.org) para obter o status mais recente em todo o processo de votação.

> Passo 14: Defina os Votos dos seus tickets através da Stakepool

Ao usar uma stakepool, qualquer ticket que você compre tem seus direitos de voto delegados a essa stakepool. Por padrão, a pool votará como quiser com seus ingressos. Mas você poderá mudar o voto de seus tickets ao seu critério.

Você pode definir os votos de seus bilhetes através da interface de tickets da stakepool. Abaixo está uma captura de tela da página [https://teststakepool.decred.org/tickets](https://teststakepool.decred.org/tickets). Na parte inferior da seção "Live / Immature" desta página, você verá as configurações de voto. Você só pode editar os votos de *todos* os seus ingressos de uma só vez através da interface do pool. Os tickets exibidos abaixo foram definidos como "Sim" para "Previous Block Valid?" E "Sim" para "Increase Block Size from 1.0 MiB to 1.25MB" o que resultou em um voto de valor 5. 

<img src="/img/testnet-voting_votebit-setting.jpg">

## Uma explicação sobre os votos (Votebits)

Abaixo você verá um screenshot de todos os valores importantes de um votebit para o voto versão 4:

<img alt="Gráfico explicando os valores do voto de um voto versão 4." src="/img/testnet-voting_vote-version-4.jpg">

Esta tela é bem auto-explicativa. Na interface do pool, se um usuário selecionou "Sim" para o aumento do tamanho do bloco e "Sim" para o bloco anterior ser válido, seus votos de voto serão definidos como "5".

Abaixo está uma captura de tela mostrando onde os Votebits e  a Versão do Voto podem ser encontrados dentro de uma transação de voto através do explorador de blocos em [https://testnet.decred.org](https://testnet.decred.org). Este voto foi emitido com um valor 5, conforme observado pelo 2º output da transação. 

<img src="/img/testnet-voting_vote-version-and-votebits.jpg">

Você pode facilmente verificar seus votos clicando no Hash da transação de qualquer um de seus tickets na seção "Voted Tickets" do site [https://teststakepool.decred.org/tickets](https://teststakepool.decred.org/tickets). (Note: seu voto *pode* ser exibido como V0 [Versão 0] devido a um bug no código da Stakepool - este bug está sendo investigado e pode ser resolvido antes deste guia ser publicado.)

## Hard Fork Demo Website

Com o propósito de mostrar o status da implementação da nova votação o site, [https://hardforkdemo.decred.org](https://hardforkdemo.decred.org) foi criado. Cada etapa pode ser visualizada pelos gráficos e pelas explicações.
