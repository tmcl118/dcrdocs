# <i class="fa fa-firefox"></i> **Guia de uso cliente Web**

---

Uma carteira web simples está disponível para usuários que não querem instalar algum software adicional no seu computador. Baseia-se na
[Copay](https://github.com/bitpay/copay) com alterações específicas para a Decred, que podem ser encontradas em [https://wallet.decred.org](https://wallet.decred.org)

Você precisar saber algumas coisas antes de usar o cliente da web:

* Você não poderá [fazer mineração PoS](/mining/proof-of-stake.md) com ela.
* Sua carteira é mantida inteiramente no armazenamento local do seu navegador web. Isso significa que se você excluir seus arquivos do armazenamento local, você excluirá sua carteira e deverá recriá-la a partir de sua seed.
* A segurança da sua carteira depende inteiramente da segurança do seu navegador.
* Você pode colocar uma senha em sua carteira para evitar o envio de fundos, mas qualquer outro acesso depende inteiramente dos controles de acesso do seu computador, não no servidor ou quaisquer detalhes de login.

---

## **<i class="fa fa-plus-circle"></i> Criando sua carteira cliente web**

> Primeiro Passo

Vá até [https://wallet.decred.org](https://wallet.decred.org). Você verá a tela com os `Termos e Condições`. Tenha atenção ao seguinte:

Assim como a carteira de linha de comando, se você perder sua seed ou sua senha para enviar fundos, você perderá o acesso à sua carteira. Não existe  a possibilidade de redefinição de senha. Observe também que todas as transações no Decred são irreversíveis por padrão. Se você acidentalmente enviar fundos para o endereço errado, você precisará pedir ao destinatário para enviá-los de volta.  Nem mesmo os desenvolvedores conseguem reverter as transações. Clique em "I Agree" uma vez que tenha lido. Agora você verá a tela de boas-vindas. Se é a primeira vez que você usa a Decred, clique em `Get Started`. Se você quiser restaurar uma carteira usada anteriormente, clique em `Import Backup`. Este guia irá assumir que você está começando, então clique em `Começar`.

> Passo Dois

Uma carteira será gerada para você e você verá esta tela:

> Passo Dois

Uma carteira será gerada e você verá a seguinte tela:

Note que abaixo de `Personal Wallet` à esquerda, diz `Testnet`. Esta carteira 
só funcionará na rede de testes da Decred. A Testnet foi desenvolvida para 
testes e as moedas no testnet não têm o valor. Clique no menu dropdown 
no canto superior esquerdo, depois clique em `Add wallet`. Clique 
em `Create New Wallet`. Dê um nome à sua carteira e clique em `Create New Wallet`.

> Passo Três

Sua carteira agora está criada e pronta para uso. No entanto, antes de fazer qualquer 
coisa, você deve adicionar uma senha para enviar fundos e fazer  backup da seed que 
foi usada para criar sua carteira. Isso é mais importante ainda para quem utilizar 
navegadores que não armazenam arquivos permanentemente. Os dados da sua carteira são 
armazenados no cache do navegador e podem ser facilmente excluídos. Se você estiver 
utilizando o modo de navegação anônima, ela será excluída assim que você fechar o 
navegador. **SEM A SENHA E A SEED VOCÊ PERDERÁ ACESSO A TODOS OS FUNDOS EM SUA CARTEIRA** 
caso os dados da carteira sejam eliminados. Os fundos ainda existem na blockchain,
 no entanto, sem a chave você não poderá acessá-los.

<i class="fa fa-exclamation-triangle"></i> **NÃO USE A MESMA SEED EM DIVERSAS CARTEIRA! Visite [o FAQ de carteiras e Seeds](/faq/wallets-and-seeds.md#3-can-i-run-multiple-wallets) para verificar o motivo. É recomendável que, quando possível, um nova carteira signifique gerar uma nova seed.** 

Clique no botão `Preferences` no lado oposto ao nome da sua carteira. Ali existe  três coisas que você deve ser interessar aqui:

Opção                                | Descrição
---                                   | ---
`Wallet Alias`                        | Você consegue renomear sua carteira.
`Request Password for Spending Funds` | Pelo fato de sua carteira estar salva no cache do browser, não é necessário nenhuma senha para acessar seus fundos. Configurando uma senha aqui, você poderá se certificar de que apenas você poderá movimentar seus fundos, caso outra pessoa acesse seu navegador. Digite uma senha e clique em `Set`. Observe o alerta que informa que as senhas não podem ser recuperadas. Não é possível fazer um reset da senha na carteira. Se você perder a senha, você não conseguirá movimentar suas moedas da sua carteira ou utilizá-las para votação no proof-of-stake.

> Passo quatro

Clique em `Backup`. Você verá esta tela:

Primeiramente, leia a nota. Utilize apenas uma carteira a cada momento com
a mesma seed (Veja: [FAQ](#)). Você poderá diversas carteira instaladas em
diferentes computadores, mas somente uma deverá ser executada ao mesmo tempo
Clique em `Show Wallet Seed`. Escreva isso em um local seguro,
ou coloque isso em um documento criptografado para que você não esqueça sua senha
Esta lista de palavras é utilizada para gerar uma chave de autenticação
para sua carteira. Qualquer pessoa que possua esta seed poderá acessar seus fundos
em sua carteira.

> **MUITO IMPORTANTE**

**NÃO DÊ, EM NENHUMA CIRCUNSTÂNCIA, SUAS SENHAS PARA NINGUÉM! NEM MESMO OS DESENVOLVEDORES!**

Uma vez que tenha anotado sua seed (e ter verificado duplamente que elas estão corretas, letras maiúsculas e minúsculas são importantes), vá para a próxima etapa.

> Passo cinco

Agora que você tenha anotado suas palavras sua seed e tenha verificado, faça isso
novamente. Sério. Este passo é extremamente importante. Sem esta lista de palavras
sua carteira não poderá ser utilizada e ninguém, nem mesmo os desenvolvedores, poderão
recuperá-la. Agora que você tem certeza que armazenou a lista de palavras corretamente, 
clique em `Delete Words`. Clique em `Back` duas vezes para voltar à tela principal da carteira.

---

## **<i class="fa fa-long-arrow-right"></i> Envie fundos com o cliente web**

> Primeiro Passo

Na página principal da carteira web, clique no botão `Send` na parte inferior. 
Você será levado para esta página. Observe a seção `Advanced Options` já está 
sendo mostrada. No campo `To`, coloque o endereço Decred do destinatário.

> Passo Dois

Em `Amount`, insira o valor em DCR para enviar ao destinatário. Se você desejar, 
você poderá digitar uma mensagem opcional no campo `Note`. Pressione `Enviar`. 
A opção `Use Unconfirmed Funds` permite a você utilizar fundos que a rede sabe 
que estão sendo enviados a você, mas ainda não foi confirmado pelos 
[minerados PoW](/mining/proof-of-work.md). E se esta opção está ativada e o 
montante especificado só pode ser coberto utilizando os fundos não confirmados, 
a transação não prosseguirá até que os fundos necessários forem confirmados.

---

## **<i class="fa fa-long-arrow-left"></i> Receba fundo utilizando o cliente web**

> Passo um

Clique no botão `Receive` na parte inferior da janela. Você verá
esta tela:

Dê à pessoa que está enviando DCR a você o endereço exibido (ele começa com `Ds`) 
ou podem usar o código QR se sua carteira ou serviço aceitar. Você pode usar o 
mesmo endereço quantas vezes quiser, mas para privacidade recomenda-se que você 
gere um novo endereço de tempos em tempos. Não se preocupe em ter recebido um 
endereço duplicado. Em torno de `2.08x10^93` possíveis endereços podem ser gerados,
 então provavelmente os endereços Decred se esgotarão apenas após o apocalipse 
 do universo.

