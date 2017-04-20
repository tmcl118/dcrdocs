# **Guia para iniciantes**

Última atualização para v0.8.2

---

## **Bem-vindo à Decred**

Bem-vindo ao mundo da Decred! Nós sabemos que iniciar em qualquer nova criptomoeda pode ser difícil, e nós queremos tornar esta jornada a mais fácil possível. As informações sobre a Decred estão bem documentadas e completas, desde a informação mais básica como, por exemplo, “como posso enviar Decred”, até coisas muito técnicas como “por que vocês escolheram a função hash BLAKE-256, e qual a diferença para a função hash Merkle-Damgård?”.

Para você não ficar perdido no meio de toda a informação disponível, nós criamos este guia para iniciantes sobre a documentação. Clicando nos links ao fim da página, você irá aprender sobre como instalar, configurar e utilizar os programas da Decred; como adquirir DCR; como votar através da Proof-of-Stake; como utilizar o explorador de blocos; e como configurar o software para utilizar na rede de testes. 

---

## **Aplicativos**

Abaixo você encontrará a lista de aplicativos disponíveis atualmente, com uma tabela mostrando a disponibilidade de cada um, em relação aos diversos sistemas operacionais.

**Paymetheus**: A única interface gráfica para Windows na versão v0.8.2. <br />
**dcrd**: Um node daemon, este aplicativo de linha de comando lida com o gerenciamento dos blocos e o consenso <br />
**dcrwallet**: Uma carteira daemon, este aplicativo de linha de comando lida com o gerenciamento dos endereços e transações <br />
**dcrctl**: Um cliente de Chamada remota de procedimento (RPC, sigla em inglês), é um aplicativo de linha de comando, utilizado para controlar o dcrd e a dcrwallet através de comandos RPC <br />
**Decrediton**: Uma interface gráfica multi-plataforma em ALPHA na versão v0.8.2

|           | Paymetheus | dcrd | dcrwallet | dcrctl | Decrediton |
| ---------:|:----------:|:----:|:---------:|:------:|:-----------:|
| Windows   | X          | X    | X         | X      |             |
| macOS     |            | X    | X         | X      | X           |
| Linux     |            | X    | X         | X      | X           |
| Outros UNIX|            | X    | X         | X      |             |

"Outros UNIX" atualmente incluem vários *BSDs and Solaris/illumos.

Observação: você irá observar que uma das muitas diferenças entre a Decred e outras criptomoedas conhecidas: a carteira daemon e o node daemon são separados. Muitas moedas executam estas duas funções em um único daemon. Para quem optar por utilizar as interfaces de linha de comando, isso significará que você deverá executar o `dcrd` para a funcionalidade full node, e o `dcrwallet` para armazenar suas DCR’s, fazer transações e participar da mineração e/ou votação Proof-of-Stake.

---

## **Guias de instalação**

Para iniciar, escolha uma das instalações disponíves abaixo, para seu sistema operacional:

* [Paymetheus](/getting-started/install-guide.md#paymetheus)

* [Conjunto de linha de comando **via dcrinstall**](/getting-started/install-guide.md#dcrinstall) - Observação: o método `dcrinstall` é o mais fácil e rápido caminho para executar o node e a carteira. Nós o recomendamos, e os guias de configuração abaixo assumem que você utilizou este método.
* [Decrediton (ALPHA)](/getting-started/install-guide.md#decrediton)

---

**Observação:** Todos os guias abaixo podem ser encontrados do menu navegação com os mesmos nomes.

## **Utilizando a Paymetheus**

Os guias abaixo, na sequência, irão auxiliá-lo a iniciar com a Paymetheus:

* [Configuração da Paymetheus](/getting-started/user-guides/paymetheus.md)
* [Utilizando a Paymetheus](/getting-started/user-guides/using-paymetheus.md)

## **Utilizando a Decrediton**

O guia abaixo, irá auxiliá-lo a utilizar a Decrediton:

* [Configurando a Decrediton](/getting-started/user-guides/decrediton-setup.md)

## **Utilizando linhas de comando**

Os guias abaixo, em sequência, irão auxiliá-lo a iniciar com os aplicativos de linha de comando (`dcrd`, `dcrwallet`, `dcrctl`):

* [Diferenças entre linhas de comando](/getting-started/cli-differences.md)
* [Início básico](/getting-started/startup-basics.md)
* [Configuração do dcrd](/getting-started/user-guides/dcrd-setup.md)
* [Configuração da dcrwallet](/getting-started/user-guides/dcrwallet-setup.md)
* [Utilização básica da dcrctl](/getting-started/user-guides/dcrctl-basics.md)

## **Guias gerais**

Os guias a seguir são independentes dos aplicativos:

* [Adquirindo DCR](/getting-started/obtaining-dcr.md)
* [Utilizando o Explorador de Blocos](/getting-started/using-the-block-explorer.md)
* [Guia de mineração Proof-of-Stake](/mining/proof-of-stake.md)
