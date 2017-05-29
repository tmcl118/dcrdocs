# **<i class="fa fa-cubes"></i> Utilizando o Block Explorer**

---

## **<i class="fa fa-info-circle"></i> Visão Geral**

Um block explorer baseado no
[Insight](https://github.com/bitpay/insight-ui) é utilizado na rede da Decred. Todos os blocos e transações na blockchain da Decred podem ser visualizados através do block explorer, localizado no link
[`https://mainnet.decred.org`](https://mainnet.decred.org) e
[`https://testnet.decred.org`](https://testnet.decred.org) para a rede de testes.  Abaixo você pode encontrar uma breve detalhamento das informações encontradas lá.

Item           | Explicação
---            | ---
`Height`       | O número do bloco.
`Age`          | Quanto tempo o bloco foi inserido na blockchain.
`Transactions` | O número de transações incluídas no bloco.
`Votes`        | O número de votos da proof-of-stake incluídos no bloco.
`Fresh Stake`  | O número de novos tickets comprados neste bloco.
`Size`         | O tamanho (em bytes) do bloco.

Abaixo de `Latest Transactions`, você poderá ver o ID da transação (txid) e o valor (em DCR) transmitido pela rede.

---

## **<i class="fa fa-cube"></i> Blocos**

Os blocos podem ser encontrados procurando seu número block height, clicando em `Height` da página inicial, ou `BlockHash`. Os blocos mais antigos terão o block height menores. A parte de cima de um bloco mostra informações relevantes sobre este bloco específico. Estas informações incluem: a block height, o BlockHash e vários parâmetros importantes da rede, descritos abaixo:

Item                     | Explicação
---                      | ---
`Number of Transactions` | O número de transações padrão (DCR enviadas de um usuário ao outro).
`Height`                 | Em que altura da blockchain este bloco se encontra.
`Block Reward`           | A quantidade de novas DCR mineradas neste bloco.
`Timestamp`              | O tempo que este bloco foi criado por um minerador e incluído na blockchain.
`Merkle Root`            | Um valor hash de todas as transações hashes incluídas neste bloco.
`Stake Root`             | Um valor hash de todas as transações hashes relacionadas a Stake. Isso inclui compra de tickets, votos, and tickets revogados.
`VoteBits`               | (1) Bloco foi aprovados pelos mineradores proof-of-stake. (2)Bloco foi vetado pelos mineradores proof-of-stake e todas as transações não relativas a stake do bloco foram invalidadas, além do minerador proof-of-work e o subsídio.
`Final State`            | O valor final do gerador de números aleatórios usado para a seleção do ticket.
`Voters`                 | O número de votos proof-of-stake com sucesso registrados no bloco. O valor máximo é 5.
`Fresh Stake`            | O número de tickets comprados confirmados neste bloco.
`Revocations`            | O número de tickets que não conseguiram votar e foram revogados.
`PoolSize`               | O númeor total de tickets proof-of-stake ativos.
`Difficulty`             | A dificuldade da rede proof-of-work.
`SBits`                  | O valor de um ticket proof-of-stake.
`Bits`                   | Uma versão compacta da dificuldade da rede no momento em que o bloco foi minerado.
`Size`                   | O tamanho do bloco (em bytes).
`Version`                | A versão do bloco.
`Nonce`                  | O valor utilizado pelo minerador para encontrar a solução do bloco.

## **<i class="fa fa-exchange"></i> Transações**

Esta seção lista todas as transações que foram mineradas neste bloco. As transações são escolhidas a partir do mempool de rede, dando preferência para a taxa mais alta. Todas as transações encontradas do bloco seguem esta ordem: transações padrão (transferência peer-to-peer), votos proof-of-stake, compra de tickets proof-of-stake. As seções a seguir explicarão cada tipo de transação.

---

### Transações Padrão

Aqui estão as informações incluídas em uma transação padrão não confirmada que passou pela rede Decred. Não confirmada significa que ainda não foi incluída em um bloco, o que implica que é uma transação recente ou foi enviada com uma taxa muito baixa.

Item                | Explicação
---                 | ---
`Size`              | O tamanho da transação em bytes.
`Fee rate`          | A taxa coletada pela rede (por kB).
`Received Time`     | O horário que  rede recebeu a transação.
`Mined Time`        | O horário que o minerador incluiu a transação em um bloco.
`Included in Block` | O número do bloco que a transação faz parte.

Note que `Received Time`, `Mined Time` e `Included in Block` não terão um valor até que um minerador confirme a transação. Dependendo das taxas no mempool, isso levará cinco minutos em média. Uma vez que exista pelo menos uma confirmação, a transacção é considerada completa.

---

### Compra Tickets

Para uma compra de ticket (stake submission) há algumas diferenças para uma transação padrão.

Observe a diferença em alguns detalhes: A palavra `Ticket` aparece acima da endereço da carteira do remetente à esquerda, e as palavras `Subsidy Commitment` aparecem à direita. Este usuário comprou um bilhete de por 8.75411638 DCR e recebeu um montante 7.15994209 DCR. O endereço listado à esquerda sob `Ticket` é o endereço que contém os fundos usados para comprar este ticket. O primeiro output à direita é o endereço que mantém o direito de voto para este ticket específico. O segundo output, `Subsidy
Commitment`, é o endereço para onde a recompensa irá. Isso ainda não é mostrado pelo explorador de blocos neste momento. O terceiro output é o endereço onde a diferença desta transação será enviada.

---

### Votos Proof-of-stake

Observe os termos para identificar os detalhes desta seção: `Vote`, `Stake
Base`, `Block Commitment`, e `Vote Bits`:

Essas palavras-chave indicam que esta transação é um voto que foi lançado na rede por um dono de um ticket de proof-of-stake. Neste exemplo, o usuário tinha  adquirido um ticket por 8.99472311 DCR e foi enviado 10.82959184 DCR após o voto ter sido lançado nesta transação.
