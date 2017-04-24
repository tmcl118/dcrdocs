# **Decrediton Setup Guide**

Última atualização para versão v0.8.2.

Este guia tem por objetivo auxiliar na configuração do aplicativo `Decrediton`. 

**Pré-requisitos:**

- Utilize o [guia de instalação da Decrediton](/getting-started/install-guide.md#decrediton) para instalar a `Decrediton`.

---

A `Decrediton` é uma interface gráfica para o software `dcrwallet`. Quando executada, ela inicia automaticamente  as próprias instâncias do `dcrd` e `dcrwallet` em segundo plano - e ela não abrirá caso já esteja sendo executada alguma instância do `dcrd`. Por favor note que a versão 0.8.2, é uma versão alpha - existem alguns bugs já conhecidos que estão sendo corrigidos.

Observação: a qualquer momento no uso da Decrediton, ela poderá parar de responder ou travar na tela de carregamento. E isso normalmente é consertado quando o aplicativo é reiniciado.

---

## **Informação importante**

Durante o processo de criação da carteira, o sistema irá fornecer uma sequência de 33 palavras, conhecidas como "seed phrase". Essa seed phrase é a senha privada de sua carteira Você poderá utilizar esta seed phrase para resgatar suas chaves privadas, o histórico de transações e seu saldo, utilizando qualquer carteira Decred, em qualquer computador.

Isso significa que *qualquer pessoa* que souber sua seed poderá utilizar isso para resgatar suas chaves privadas, histórico de transações e seu saldo, sem o seu conhecimento ou autorização. Por esta razão, é de extrema importante que você mantenha sua seed phrase em um local segura. Trate esta seed como você trata uma chave física de um cofre. Se você perder a seed phrase, você perderá o acesso à sua carteira e todo seu saldo nela contido. Isto não poderá ser recuperado por ninguém, nem mesmo pelos desenvolvedores da Decred. É recomendável que você anote as palavras em um papel e armazene em um local seguro. Caso opte por manter em seu computador, o melhor é manter a informação em um documento criptografado (não se esqueça da senha) caso o seu computador seja roubado.

**IMPORTANTE: NÃO DÊ, EM NENHUMA CIRCUNSTÂNCIA, SUA SEED OU A CHAVE HEX ASSOCIADA A NINGUÉM! NEM MESMO AOS DESENVOLVEDORES**

---

Toda vez que abrir a `Decrediton`, você receberá esta mensagem:

    Decrediton is currently under heavy development and in an alpha-state. While we have tested the code thoroughly, we suggest using caution on Mainnet. Use at your own risk!

## **Criando uma nova carteira**

Após clicar em "OK, I Understand" na mensagem, você verá a informação "Create a Wallet".

O passo "Create a Wallet" por padrão irá encaminhar para a opção "New Seed". Clique em "Existing Seed" caso já possua uma seed que queira usar, e siga as instruções. Este guia assume que você não possui uma seed e irá continuar utilizando a opção "New Seed". Por favor, revise as [informações importantes](#critical-information) sobre seeds acima.

1. Registre a seed que está sendo mostrada na caixa de texto (você terá que digitar a seed na próxima tela).

2. Clique em "Continue"

3. Confirme sua seed, e crie a private passphase(senha privada) da sua carteira. Esta senha será utilizada para desbloqueio de sua carteira quando for criar uma transação.

4. Clique em "Create Wallet"

5. Você deverá ver um círculo azul girando. Ele irá girar até que o `dcrd` tenha sincronizado totalmente a blockchain. Em computadores que não tenham carregado o `dcrd`, este processo poderá levar de 1 a 2 horas em computadores novos (e poderá levar várias horas em máquinas antigas). Você poderá verificar o monitor de atividade de processos e observar se o processo `dcrd` - está consumindo um percentual considerável do CPU, em caso positivo é sinal que está havendo a sincronização. Em caso negativo, você deverá reiniciar a Decrediton para sair desta tela.

## **Abrindo a carteira**

Após a sincronização da blockchain, você deverá ver a página "Opening Wallet". Aqui, você precisará colocar a private passphrase e a carteira irá escanear todos os blocos recentes para encontrar as transações pertencentes aos seus endereços. Aguarde até a barra de processo estar completa. A Decrediton deverá carregar a página Overview onde consta o seu saldo disponível (Available Balance) e as últimas transações (Recent Transactions).

---

