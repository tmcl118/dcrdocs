# **dcrctl Basics**

Última atualização para v0.8.2.

Este guia tem o objetivo de auxiliar na configuração do aplicativo do `dcrctl` utilizando [startup flags](/getting-started/startup-basics.md#startup-command-flags). 

**Pré-requisitos:**

- Utilize a última versão do [dcrinstall](/getting-started/install-guide.md#dcrinstall) para instalar o `dcrctl`. Passos adicionais serão necessários caso você utilize outro método de instalação.
- Veja como os comandos de inicialização se diferenciam para as Shells: Prompt de Comando (Windows) e para o Bash (OSX/Linux), e como se diferenciam as pastas de instalação [aqui](/getting-started/cli-differences.md).
- [Configure o dcrd](/getting-started/user-guides/dcrd-setup.md) e execute ele em segundo plano.
- [Configure a dcrwallet](/getting-started/user-guides/dcrwallet-setup.md) e execute ela em segundo plano.

---

`dcrctl` é o cliente que controla o `dcrd` e a `dcrwallet` através de chamada de procedimento remoto (RPC - Remote Call Procedure). Você pode usar o `dcrctl` para muitas coisas, por exemplo, verificar seu saldo, comprar tickets, criar transações e verificar informações da rede.

**OBSERVAÇÃO:** Este guia usa exemplos, de comandos para qualquer sistema operacional. Reveja os pré-requisitos para determinar se você deve usar `./dcrctl` ou `dcrctl.exe` em vez de `dcrctl`, por exemplo.

---

> Configure nome de usuário e senha do RPC

Os comandos enviados para `dcrd` ou` dcrwallet` exigirão que o nome de usuário/senhas do RPC sejam configurados nos arquivos de configuração.

Se você usou o [`dcrinstall`](/getting-started/install-guide.md#dcrinstall), seus arquivos de configuração já estão configurados com o nome de usuário/senha do RPC para o `dcrd`, a `dcrwallet` e o `dcrctl`.

Se você não usou `dcrinstall`, você precisará ativar as configurações mínimas nos arquivos de configuração. Siga [este guia](/getting-started/startup-basics.md#minimum-configuration) para fazer isso.

---

## Comandos dcrctl

Você precisará executar comandos dcrctl em uma janela de shell separada (Prompt de Comando/Bash).

Para dar comandos para a `dcrwallet`, você precisará usar `dcrctl --wallet <command>`.

Para dar comandos para o `dcrd`, você precisará usar `dcrctl <command>`.

Para ver uma lista completa de comandos que `dcrctl` pode enviar para `dcrd` e `dcrwallet`, emita o seguinte comando no shell:

```no-highlight
dcrctl -l
```

Isso retornará uma longa lista de comandos, divididos por aplicativo. Os comandos na seção superior são da `dcrd` e os comandos na seção inferior são da `dcrwallet`. Você pode descobrir mais sobre um comando individual da `dcrwallet` digitando o seguinte os comandos:

```no-highlight
dcrctl help --wallet <command>
```

Ou o seguinte comando para o `dcrd`:

```no-highlight
dcrctl help <command>
```

---

## Desbloquear sua Carteira

Algumas funcionalidades da `dcrwallet` requerem que a carteira seja desbloqueada.

O comando para desbloquear sua carteira é:

```no-highlight
dcrctl --wallet walletpassphrase <private passphrase set during wallet creation> 0
```

Aqui, estamos especificando para `dcrctl` como enviar o comando para `dcrwallet` usando a flag `--wallet`. O comando é `walletpassphrase` que aceita dois parâmetros, sua senha privada e um limite de tempo. Especificar `0` para um limite de tempo desbloqueia a `dcrwallet` sem tempo limitado. Observe, no entanto, que isso só desbloqueia a carteira para a sessão atual. Se você fechar a janela onde a carteira está sendo executada, ou parar/reiniciar a `dcrwallet`, você precisará desbloqueá-la novamente na próxima vez que você iniciá-la.

Se o comando foi bem sucedido, você não receberá uma confirmação do `dcrctl`, mas se você olhar para sua sessão `dcrwallet`, constará a mensagem:

```no-highlight
[INF] RPCS: The wallet has been unlocked without a time limit.
```

Observação: Uma vez que o desbloqueio da carteira é necessário para muitas funções da `dcrwallet`, a `dcrwallet` pode ser iniciada com a flag `--promptpass` ou configuração `promptpass=true` no `dcrwallet.conf` (discutido [aqui](/advanced/storing-login-details.md#dcrwalletconf)).


---

## Verificando seu saldo

Para enviar o comando `getbalance` para a `dcrwallet` utilizando o `dcrctl`, digite o seguinte em seu shell:

```no-highlight
dcrctl --wallet getbalance
```

Isso retornará todos os saldos de todas as suas contas.

---

## Obtendo um novo endereço de recebimento

Para enviar o comando `getnewaddress` para a `dcrwallet`, utilizando o `dcrctl`, digite o seguinte em seu shell:

```no-highlight
dcrctl --wallet getnewaddress
```

Isso gerará e retornará um novo endereço de pagamento. Para minimizar a reutilização de endereços, use este comando para obter um novo endereço para cada transação que deseja receber.

---

## Enviando DCR

Para enviar DCR para um endereço, dê o comando `sendtoaddress` para a `dcrwallet` utilizando o `dcrctl`. Digite o seguinte em seu shell, preenchendo o endereço de recebimento e quantidade para enviar:

```no-highlight
dcrctl --wallet sendtoaddress <address> <amount>
```

Se for bem sucedido, `dcrctl` retornará um hash da transação que pode ser usado para assistir a transação no site oficial [Decred Block Explorer](/getting-started/using-the-block-explorer.md).

---

## Verificar estatísticas da rede

Há muitos comandos diferentes para verificar diferentes dados de rede. Aqui vamos abordar o envio de `getinfo` para o `dcrd` e `getstakeinfo` para a `dcrwallet`.

Para obter informações sobre o seu node `dcrd` local, dê o comando `getinfo` para o `dcrd` usando o `dcrctl`. Digite o seguinte em seu shell:

```no-highlight
dcrctl getinfo
```

Para obter informações sobre a rede Proof-of-Stake, dê o comando `getstakeinfo` para a `dcrwallet` utilizando o `dcrctl`. Digite o seguinte em seu shell:

```no-highlight
dcrctl --wallet getstakeinfo
```

---

## Comandos Adicionais

Outros comandos também podem ser encontrados na página [Opções de Programa](/advanced/program-options.md).

---