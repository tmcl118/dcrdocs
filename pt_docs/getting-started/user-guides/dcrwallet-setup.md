# **Guia de configuração da dcrwallet**

Última atualização para v0.8.2.

Este guia tem o objetivo de auxiliar na configuração do aplicativo da `dcrwallet` utilizando [startup flags](/getting-started/startup-basics.md#startup-command-flags). 

**Pré-requisitos:**

- Utilize a última versão do [dcrinstall](/getting-started/install-guide.md#dcrinstall) para instalar a `dcrwallet`. Passos adicionais serão necessários caso você utilize outro método de instalação.
- Veja como os comandos de inicialização se diferenciam para as Shells: Prompt de Comando (Windows) e para o Bash (OSX/Linux), e como se diferenciam as pastas de instalação [aqui](/getting-started/cli-differences.md).
- [Configure o dcrd](/getting-started/user-guides/dcrd-setup.md) e execute ele em segundo plano.

---

A `dcrwallet` é uma daemon que controla as funcionalidades da carteira Decred para um usuário. Ela gerencia todas suas contas, endereços e transações; Além de rastrear as transferências de moeda entre os endereços, e permitir que os usuários participem nas votações Proof-of-Stake.

Para executar a `dcrwallet`, um arquivo `wallet.db` deve existir dentro da pasta `dcrwallet`. Para que este arquivo exista, você deverá criar uma nova carteira. O `dcrinstall` inicia automaticamente o processo de criação. Caso você delete o arquivo wallet.db ou tenha utilizado outro processo de instalação, você terá que executar[o comando manual para criação da carteira](#manual-wallet-creation-command).

---

## **Informação importante**

Durante o processo de criação de sua carteira, você receberá uma seqüência de 33 palavras conhecidas como seed. A seed é essencialmente a chave privada para sua carteira. Você será capaz de usar a seed para restaurar suas chaves privadas, histórico de transações e saldos usando qualquer carteira Decred em qualquer computador.

Isso significa que *qualquer pessoa* que conheça sua seed pode usá-la para restaurar suas chaves privadas, histórico de transações e saldos para uma carteira Decred no computador, sem o seu consentimento. Por esta razão, é de extrema importância manter sua seed segura. Cuide da seed da mesma maneira que você cuidaria da chave física de um cofre. Se você perder sua seed, você poderá perder permanentemente o acesso à sua carteira e todos os fundos dentro dela. E isso não pode ser recuperado por ninguém, nem mesmo pelos desenvolvedores da Decred. É recomendável que você anote num papel e armazene em algum local seguro. Se você decidir mantê-lo em seu computador, recomendamos que guarde em um documento criptografado (não se esqueça a senha) caso o arquivo no seu computador seja roubado.

Every seed phrase is also associated with a 64 character seed hex. The seed hex functions the same way as the seed phrase - `dcrwallet` will accept it when attempting to restore your wallet. It is also important to keep your seed hex secure.

**LEMBRETE: NÃO DÊ, SOB QUALQUER CIRCUNSTÂNCIA, SUA SEED OU A O CÓDIGO HEX ASSOCIADOS À SUA CARTEIRA A NINGUÉM! NEM MESMO AOS DESENVOLVEDORES DA DECRED!**

---

## **Comando manual para criação da carteira**

Se você ainda não tiver um arquivo `wallet.db` armazenado no diretório inicial da `dcrwallet`, você deverá executar o comando `dcrwallet --create`. As etapas para isso são:

1. Abra uma nova janela do seu Shell (Bash/ Prompt de comando/etc, ..).
2. Navegue até o diretório do executável `dcrwallet`.
3. Insira o comando `dcrwallet --create` (verifique os pré-requisitos acima se não tiver certeza se você deve usar`./dcrwallet` ou `dcrwallet.exe` para o comando anterior). 

---

## **Passo a passo da criação da carteira**

Durante esse processo, você definirá uma chave privada, e opcionalmente, definir uma chave pública, além de registrar sua seed. Para fazer isso, siga as etapas abaixo:

> Definir as chaves para a sua carteira

Se o comando `dcrwallet --create` tiver sido executado com êxito, você deve ser recebido pelo seguinte texto:

```no-highlight
Enter the private passphrase for your new wallet:
```

Esta primeira chave, e a chave privada, é a que você usará para desbloquear sua carteira para criar transações ou votar na Proof-of-Stake. Use uma senha única e forte. Esta senha também protege as chaves privadas dentro do arquivo da sua carteira, protegendo-o de roubo.

Depois de verificar sua chaves privada, você deverá ver a seguinte mensagem no prompt:

```no-highlight
Do you want to add an additional layer of encryption for public data? (n/no/y/yes) [no]:
```

Esta última chave é opcional. Ela é usada para criptografar todos os dados públicos (transações e endereços) dentro de seu arquivo da sua carteira, portanto, se ele for roubado, quem roubou não poderá vincular você às transações.

> Grave sua Seed

Antes de criar uma nova seed para sua carteira, consulte a seção [Informações críticas](/getting-started/user-guides/dcrwallet-setup.md#critical-information).

Depois de definir sua chave privada e sua chave pública (opcional), você verá a seguinte mensagem no prompt:

```no-highlight
Do you have an existing wallet seed you want to use? (n/no/y/yes) [no]:
```

Este guia assume que você não tem uma seed, então continue pressionando `Enter`, que responderá ao prompt com o padrão `[no]`. NOTA: Se pretender restaurar a sua carteira utilizando a sua seed, basta introduzir `[yes]` aqui e seguir as instruções apresentadas na tela.

<i class="fa fa-exclamation-triangle"></i> **NÃO USE A MESMA SEED EM DIFERENTES CARTEIRA! Visite [o FAQ sobre Carteiras e Seeds](/faq/wallets-and-seeds.md#3-can-i-run-multiple-wallets) para ver por que isso é importante. Recomenda-se que, sempre que possível, uma carteira nova signifique gerar uma nova semente.**

Depois de responder `[no]`, sua seed (seed para gerar carteira) e o código HEX será exibido na janela. Leia a seção IMPORTANTE exibida imediatamente após o HEX.

É importante ressaltar o quão importante é salvar sua seed em um local seguro, então se você não tiver isto em mente, por favor, revise a seção [Informações importantes](/getting-started/user-guides/dcrwallet-setup.md#critical-information) novamente.

Depois de ter anotado a seed e o HEX digite `OK` e pressione `Enter`. NOTA: se você não anotou a seed, antes de continuar você [deve começar este processo](/getting-started/user-guides/dcrwallet-setup.md#create-a-new-wallet) e depois [deletar o arquivo da carteira](/advanced/deleting-your-wallet.md)

Depois de digitar `Enter`, deverá ver a seguinte mensagem:

```no-highlight
Creating the wallet...
The wallet has been created successfully.
```

A carteira será então criada. Isso pode levar alguns minutos se você tiver um computador lento.

---

## **Executando a dcrwallet**

Para executar a `dcrwallet`, primeiro você deve ter [criado sua carteira](#wallet-creation-walkthrough) e
[o dcrd conectado à rede Decred](/getting-started/user-guides/dcrd-setup.md#connect-to-the-decred-network).

> Configurar nome de usuário e senha do RPC

Se você usou [`dcrinstall`](/getting-started/install-guide.md#dcrinstall), seus arquivos de configuração já estão configurados com o nome de usuário/senha do RPC para o `dcrd`, a `dcrwallet` e o `dcrctl`.

Se você não usou o `dcrinstall`, você precisará ativar as configurações mínimas em seus arquivos de configuração. Siga [este guia](/getting-started/startup-basics.md#minimum-configuration) para fazer isso.

> Iniciar dcrwallet

Com os arquivos de configuração corretamente configurados, abra outra janela no shell em seu diretório da Decred (ou use a última janela onde você acabou de criar sua carteira). Digite o seguinte comando (revise o guia Pré-requisitos para verificar o comando exato, dependendo do aplicativo do seu sistema operacional/Shell):

```no-highlight
dcrwallet
```

Seu `dcrwallet` agora se conectará à rede via `dcrd`. Ele começará a verificar a rede para seus endereços ativos, o que pode levar alguns minutos em computadores lentos. Eventualmente começará a mostrar linhas como:

```no-highlight
[INF] WLLT: Connecting block 0000000000002004ea8fa74af334cb291a22832642b5be603995683534bbb97b, height 9990
```

Isso significa que sua carteira está conectada com êxito à rede através do seu daemon.

---

Para aprender a usar `dcrd` e` dcrwallet`, visite o guia [básico do dcrctl](/getting-started/user-guides/dcrctl-basics.md). Você vai aprender a desbloquear sua carteira, enviar e receber DCR usando o `dcrctl`, verificar o seu saldo e verificar várias estatísticas da rede.
