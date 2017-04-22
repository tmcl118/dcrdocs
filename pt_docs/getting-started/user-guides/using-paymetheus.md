# **Paymetheus, a carteira Windows** #
Este guia assume que você já configurou a carteira Paymetheus usando [este guia](paymetheus.md).

---

## **Overview** ##
Esta seção fornece um rápido resumo do total de DCR que você possui ("utilizáveis"e "tavados"), número de consta e transações, bem como uma listas com suas atividades recentes.  

![Overview tab](/img/Paymetheus-overview.png)  

---


## **Accounts  ** ##
A seção accounts mostras as contas em sua carteira e permite você adicionar novas.
Contas na Decred funcionam como contas bancárias.
Elas permite que você diversos registros de suas DCR. Esta funcionalidade é muito útil para quem  
tem vários negócios e desejam manter contas separadas
para registros tributários, por exemplo. Transferir DCR entre contas irá criar transações na
blockchain.  

![Overview tab](/img/Paymetheus-accounts.png)  

---


## **Scripts** ##
Atualmente utilizado apenas para mineração PoS em uma pool. A partir da versão 0.8.0
a configuração do script foi automatizada. Veja a seção Purchase Tickets abaixo para mais informações.
Isto será utilizado para funcionalidades mais avançadas no futuro.  

![Scripts tab](/img/Paymetheus-import-script.png)  

---


## **Create Transaction** ##
É nesta seção onde você envia fundos para outro endereço. Copie o endereço de quem irá receber
o valor na caixa de texto e digite a quantidade de Decred que você pretende enviar.
A Fee estimada para a transação será mostrada. Você poderá clicar no botão '+' para 
enviar Decred para diversos endereços na mesma transação, caso desejar.

![Create transaction tab](/img/Paymetheus-send.png)  

---


## ** Purchase Tickets ** ##

A Paymetheus permite que você compre tickets para mineração Proof of Stake, 
utilizando a funcionalidade de compra de ticket manual. 
Observe que a Paymetheus poderá *apenas* comprar os tickets, ela não poderá
votar. Para isso você terá que configurar [PoS solo](/mining/proof-of-stake)
ou utilizar uma [stake pool](/mining/proof-of-stake.md#sign-up-for-a-stake-pool) para PoS.

> Para entrar em uma pool, forneça um endereço público que será utilizado para gerar
> um script "1-of-2 multisignature". O script multisignature será gerado pela
> pool e retornado a você com um endereço P2SH para dar direito de voto.  

Fique tranquilo se você não entender este texto acima. Ele significa que você criou um
endereço que poderá ser acessado por duas carteiras. E apenas uma carteira precisa estar disponível
para utilizar o endereço. Isso significar que a pool poderá votar em seu nome
e que você poderá votar com sua carteira, mesmo que a pool pare de funcionar.

Isto NÃO dará à pool, acesso aos seus fundos. Tudo o que você está fazendo apenas garante o
direito de voto à pool. A pool não acessa seus fundos. 

É recomendável que gere uma nova conta quando entrar em uma stake pool. Isso porque
em caso de um problema ou fechamento da pool, será seguro dar sua senha privada para outra
stake pool, pois a conta fica responsável apenas por votar e nada mais.  

As stake pools oficiais estão [listadas aqui](/mining/proof-of-stake#sign-up-for-a-stake-pool).
Todas as stake pools executam o mesmo código base, mas devem se diferenciar na quantidade de 
servidores redundante disponíveis. Quanto maior a quantidade de servidores redundantes
menor a quantidade de votos perdidos (missed votes) (apesar de que todas as pools já perderam votos
a grande quantidade de votos perdidos é causada por mineradores PoW (pode acontecer que eles encontrem a solução 
para o bloco muito rapidamente, que os votos não tiveram tempo para se propagar na rede). Para assegurar que uma pool 
não se torne muito grande, é recomendável que você se junte a uma pool pequena. Apesar de uma pool não poder acessar seus fundos, eles PODEM votar contra sua vontade. Fazendo isto, eles poderão ser listados à blacklist rapidamente,
mas mantendo todas as pools bem pequenas, significa que cada operador de pool trapaceiro, terá uma grande dificuldade
de influenciar em qualquer voto.
Distribuir tickets em diversas pools, torna a rede cada vez mais descentralizada.

![Creating voting account](/img/Paymetheus-create-voting-account.png)  

Existe uma quantidade razoável de informação por aqui, portanto iremos revisar cada uma das opções.

* **Ticket difficulty** - o preço atual de um ticket.
* **Blocks until retarget** - quando esse valor atingir 0, um novo valor para os tickets será calculado.
* **Source account** - esta conta que irá comprar os tickets e receber a recompensa.
* **Tickets to purchase** - a quantidade de tickets a comprar.
* **Ticket fee (DCR/kB)** - os tickets são inseridos à pool de votação pela ordem de suas fee's. Quando a demanda 
                        por tickets for alta, você terá que aumentar este valor, para ter os tickets aceitos.
						Você poderá verificar as tickets fee's [aqui](https://www.dcrstats.com).
* **Split fee (DCR/kB)** - a Paymetheus utiliza uma transação “split” para evitar que seu saldo seja bloqueado separando
                       o valor exato necessário para o ticket, do seu saldo na carteira. A transação “split” precisa ser confirmada pelo menos uma vez, antes de você poder reutilizar seu saldo. Isso poderá bloquear todo seu saldo por vários minutos enquanto a confirmação não ocorre. Sem a "split" você terá que aguardar pela confirmação da transação do seu ticket, o que poderá levar algumas horas.
                       A fee poderá ser 0.01. Isso não afeta suas chances de comprar tickets ou votá-los.
* **Expiry (blocks)** - as fees para compra de tickets poderão aumentar durante uma janela de compra, e você poderá se                            deparar com altas taxas. Configurando a "expiry", os tickets que não forem minerados durante o                             número de blocos configurados,xpiry, serão cancelados e você poderá tentar comprar com uma fee mais                        alta caso desejar. Se ficar vazio, a ordem de compra ficará válida até o fim da janela de compra.
* **Stake pool preference** - configuração automática com a pool de PoS. Verifique abaixo para mais informações.
* **Voting address** - o endereço Decred que irá votar. Apenas para mineração solo e mineradores com pools customizadas.
* **Pool fee address** - para quem utiliza pool customizada.
* **Pool fees (%)** - para quem utiliza pool customizada.

![Purchasing tickets](/img/Paymetheus-ticket-purchasing.png)  

Para rapidamente configurar a compra de um ticket através de uma stake pool, clique no botão 'Manage pools'. Se você ainda não clicou nele, você terá que se registrar a uma pool (veja acima). Uma vez que tenha se registrado, faça o login, encontrei sua API key, e copie. Selecione a pool que você se registrou, no menu drop down. Cole o código na caixa 'API key' e clique em 'Save'.
Você deverá ver um monte de letras e números aparecerem abaixo na caixa. Clique em 'Close'. Agora você poderá comprar tickets clicando no botão 'Purchase'!

![Manage stake pools](/img/Paymetheus-manage-stake-pool.png)
			
Observação: você poderá comprar tickets pela Paymetheus, porém ela não votará por você para isto, você deverá utilizar uma pool ou executar sua própria carteira para votar, que necessita estar online 24/7. Se você optar por minerar solo, confira o [guia de configuração do dcrd](/getting-started/user-guides/dcrd-setup.md), [o guia de configuração da dcrwallet](/getting-started/user-guides/dcrd-setup.md) e [guia de mineração PoS](/mining/proof-of-stake.md) para maiores informações.

---

## **Request Payment** ##
É aqui que você pode gerar endereços de carteira, para que elas possam enviar DCR para você. 
Simplesmente escolha a conta que deseja receber os fundos, e clique em Generate Address.
Copie o endereço (é a linha superior que incia com Ds) e compartilhe com a outra pessoa.
Os endereços Decred poderão ser utilizados quantos vezes você desejar, mas por razões de privacidade, é 
melhor gerar um novo endereço a cada transação. Existem cerca de 1.4E48 (isto é 14 seguido 47 zeros)
de endereços disponíveis, assim você não precisa se preocupar em esgotar este número.

![Request Payment](/img/Paymetheus-receive.png)  

---


## **Transaction History** ##
Esta seção mostra a lista de todas as transações que ocorreram. O hash da transação pode ser utilizado com o 
[explorador de blocos](/getting-started/using-the-block-explorer.md) para ver mais informações sobre a transação.

![Transaction History](/img/Paymetheus-transactions.png)  

---


## **Stake Mining** ##
Esta seção mostra algumas estatísticas sobre a rede PoS:

Item                         | Descrição
:-----------------------------:|:------------------------------------------------------------:
Number of live tickets       | O número total de tickets que poderão votar na rede
Number of tickets in mempool | O número total de tickets que estão aguardando para entrar na voting pool
Ticket difficulty            | O custo de 1 ticket (estornado caso o ticket seja votado ou expire)
Owned tickets in mempool     | O número de tickets na mempool
Owned live tickets           | O número de tickets que podem votar
Owned immature tickets       | O número de tickets aguardando para amadurecer antes de ir live (256 blocos, ~17 horas)
Tickets missed               | Os tickets que perderam o voto, devido à carteira de votação ou a pool estarem offline ou pela mineração PoW não ter sido feita corretamente
Tickets revoked              | Tickets que perderam o voto e tiveram o valor do ticket estornado (menos a ticket fee), deve ser o mesmo número de Tickets missed
Tickets voted                | Todos os tickets votados por esta carteira
Total subsidy earned         | Todo o subsídio em DCR recebido por esta carteira
