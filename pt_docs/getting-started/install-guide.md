# Guia de instalação

Última atualização para v0.8.2

---

Existem 5 métodos para download e instalação de software da Decred. 

* [Instalador Windows](#paymetheus) (.msi) - Este método funciona apenas para a instalação da Paymetheus em máquinas Windows.
* [dcrinstall](#dcrinstall) - Instalador automático Multi-plataforma para aplicativos de linha de comando (`dcrd`, `dcrwallet`, and `dcrctl`).
* [Decrediton](#decrediton) - Para instalação da decrediton em máquina Linux ou Mac.
* [Versões dos binários](#binary-releases) pré-compilados para instalação e configuração manual, para aplicativos de linha de comando multi-plataforma.
* Compilação do código fonte.

Os primeiros quatro métodos serão abordados aqui, o quinto poderá ser acrescentado futuramente. 

---

## **Paymetheus** 

O instalador para Windows (Arquivo `.msi`) está localizado aqui: [https://github.com/decred/decred-binaries/releases](https://github.com/decred/decred-binaries/releases). Este arquivo irá instalar a Paymetheus no seu computador na pasta Arquivos de Programas. A instalação é bem intuitiva, mas algumas instruções podem ser vistas abaixo:

1. Faça o download do arquivo correto:

    Para computadores 32-bit, faça o download do arquivo `decred_0.8.2-beta_x86.msi`. <br />
    Para computadores 64-bit, faça o download do arquivo `decred_0.8.2-beta_x64.msi` file.

2. Localize a pasta onde o arquivo foi baixado e dê dois cliques no arquivo `.msi`.

3. Siga os passos da instalação. Durante este processo você deverá aceitar o contrato de licença para o usuário final.

4. Após a instalação, os aplicativos deverão estar instalados na pasta `..\Arquivos de Programas\Decred\` e acessíveis no menu Iniciar (procure por `Decred` na lista de programas)

---

## **dcrinstall**

`dcrinstall` é um instalador e atualizador automático para os softwares da Decred. A última versão pode ser encontrada aqui: [https://github.com/decred/decred-release/releases](https://github.com/decred/decred-release/releases). São oferecidos binários para Windows, OSX/macOS, Linux, OpenBSD, and FreeBSD. A execução do arquivo irá instalar o `dcrd`, `dcrwallet`, e o `dcrctl`. São fornecidas abaixo instruções para usuários Mac, Linux e Windows, (consideramos que usuários *BSD são proficientes).

Este método é o mais recomendado, em relação ao método de instalação tradicional. O `dcrinstall` fará automaticamente o download do pacote binário assinado e pré-compilado, encontrado no GitHub, verificará a assinatura do pacote, copiará os binários presentes no pacote para uma pasta específica do sistema operacional, criará os arquivos configurados para permitir a comunicação dos 3 aplicativos, e conduzir ao processo de criação da carteira. Após a instalação do `dcrinstall`,você poderá executar o software sem a necessidade de nenhuma configuração adicional.

> OSX/macOS:

1. Faça o download do arquivo correto:

    Para computadores 32-bit, faça o download do arquivo `dcrinstall-darwin-386-v0.8.2`<br />
    Para computadores 64-bit, faça o download do arquivo `dcrinstall-darwin-amd64-v0.8.2`.

2. Torne o arquivo dcrinstall-darwin-xxxx-vx.x.x executável utilizando o terminal, e execute:

    Navegue até a pasta onde o arquivo dcrinstall foi baixado utilizando o comando `cd`, execute chmod com o modo u+x no arquivo dcrinstall, e execute o arquivo executável criado. Abaixo um exemplo dos comandos (modifique as pastas ou nome do arquivo caso seja necessário):
    
    `cd ~/Downloads/` <br />
    `chmod u+x dcrinstall-darwin-amd64-v0.8.2` <br />
    `./dcrinstall-darwin-amd64-v0.8.2`
    
3. Os binários executáveis para `dcrd`, `dcrwallet`, and `dcrctl` poderão ser encontrados na pasta `~/decred/`. Antes de completar o processo `dcrinstall`, você será levado ao processo de criação da carteira. Siga os passos que constam neste [Walkthrough para criação da carteira](/getting-started/user-guides/dcrwallet-setup.md#wallet-creation-walkthrough) do guia de instalação da dcrwallet para finalizar.

> Linux:

1. Faça o download do arquivo correto:

    Para computadores 32-bit, faça o download do arquivo `dcrinstall-linux-386-v0.8.2`<br />
    Para computadores 64-bit, faça o download do arquivo `dcrinstall-linux-amd64-v0.8.2`<br />
    Para computadores 32-bit ARM, faça o download do arquivo `dcrinstall-linux-arm-v0.8.2`<br />
    Para computadores 64-bit ARM, faça o download do arquivo `dcrinstall-linux-arm64-v0.8.2`

2. Torne o arquivo dcrinstall-linux-xxxx-vx.x.x executável utilizando o terminal, e execute:

    Navegue até a pasta onde o arquivo dcrinstall foi baixado utilizando o comando `cd`, execute chmod com o modo u+x no arquivo dcrinstall, e execute o arquivo executável criado. Abaixo um exemplo dos comandos (modifique as pastas ou nome do arquivo caso seja necessário):
    
    `cd ~/Downloads/` <br />
    `chmod u+x dcrinstall-linux-amd64-v0.8.2` <br />
    `./dcrinstall-linux-amd64-v0.8.2` 
    
3. Os binários executáveis para `dcrd`, `dcrwallet`, and `dcrctl` poderão ser encontrados na pasta `~/decred/`. Antes de completar o processo `dcrinstall`, você será levado ao processo de criação da carteira. Siga os passos que constam neste [Walkthrough para criação da carteira](/getting-started/user-guides/dcrwallet-setup.md#wallet-creation-walkthrough) do guia de instalação da dcrwallet para finalizar.

> Windows:

1. Faça o download do arquivo correto:

    Para computadores 32-bit, faça o download do arquivo `dcrinstall-windows-386-v0.8.2.exe`<br /> 
    Para computadores 64-bit, faça o download do arquivo `dcrinstall-windows-amd64-v0.8.2.exe`<br />

2.  Execute o arquivo dcrinstall.

    Você poderá fazer isso dando um clique duplo sobre o arquivo ou executando através do Prompt de Comando.
    
3. Os binários executáveis para `dcrd`, `dcrwallet`, and `dcrctl` poderão ser encontrados na pasta `%HOMEPATH%\decred\` (normalmente o %HOMEPATH% é `C:\Users\<username>`). Antes de completar o processo `dcrinstall`, você será levado ao processo de criação da carteira. Siga os passos que constam neste [Walkthrough para criação da carteira](/getting-started/user-guides/dcrwallet-setup.md#wallet-creation-walkthrough) do guia de instalação da dcrwallet para finalizar.

---

## **Decrediton**

A Decrediton é lançada com as versões dos binários e pode ser encontrada aqui: [https://github.com/decred/decred-binaries/releases](https://github.com/decred/decred-binaries/releases). A partir da v0.8.2, Decrediton está disponível apenas para Linux e Mac, e é tecnicamente uma versão alpha. Existem alguns bugs já conhecidos que estão sendo corrigidos.

> macOS/OSX

1. Faça o download do arquivo `decrediton-0.8.2.dmg`

2. Dê um clique duplo no arquivo `decrediton-0.8.2.dmg` para montar a imagem do disco.

3. Arraste o arquivo decrediton.app para o link da pasta Applications, dentro da imagem do disco.

> Linux

1. Faça o download do arquivo `decrediton-0.8.2.tar.gz`

2. Navegue até o local onde fez o download e extraia o arquivo .tar.gz:

    Gerenciador de arquivos do Ubuntu: clique com o botão direito no arquivo .tar.gz e clique em "Extrair aqui". <br />
    Terminal: utilize o comando `tar -xvzf filename.tar.gz` 
    
    Os dois procedimentos irão extrair o arquivo tar.gz em uma pasta com o mesmo nome do arquivo (`e.g. tar -xvzf decrediton-v0.8.2.tar.gz` irá extrair para `decrediton-v0.8.2`). Estando tudo correto, nesta nova pasta deverá constar um executável chamado `decrediton`.


---

## **Versões Binárias**

As últimas versões binárias lançadas poderão ser encontradas aqui: [https://github.com/decred/decred-binaries/releases](https://github.com/decred/decred-binaries/releases). Com exceção dos arquivos `.msi` and `.dmg`, eles são arquivos dos últimos binários executáveis de cada versão. Apesar de muitos deles serem prontos para descompactar e instalar, são fornecidas abaixo instruções para usuários Mac, Linux e Windows, (consideramos que usuários *BSD são proficientes).

> OSX/macOS

1. Faça o download do arquivo correto:

    Para computadores 32-bit, faça o download do arquivo `decred-darwin-386-v0.8.2.tar.gz`<br />
    Para computadores 64-bit, faça o download do arquivo `decred-darwin-amd64-v0.8.2.tar.gz`

2. Navegue até o local onde fez o download e extraia o arquivo .tar.gz:

    Finder: dê um clique duplo no arquivo .tar.gz. <br />
    Terminal: utilize o comando `tar -xvzf filename.tar.gz` 

    **Observação**: Se você estiver utilizando o Safari no macOS Sierra e tem a opção 'Abra arquivos seguros após o download' ativada, os arquivos .gz and .zip são extraídos automaticamente após o download. O comando `tar -xvzf filename.tar.gz` retorna este erro: `tar: Error opening archive: Failed to open 'filename.tar.gz'`. Utilize `tar -xvzf filename.tar` (remova o .gz do comando anterior).
    
    Os dois irão extrair o arquivo tar um uma pasta com o mesmo nome do arquivo. (`por exemplo tar -xvzf decred-darwin-amd64-v0.8.2.tar.gz` deverá extrair para `decred-darwin-amd64-v0.8.2`). A pasta deverá incluir `dcrctl`, `dcrd`, `dcrwallet`, `sample-dcrctl.conf`, `sample-dcrd.conf`, e `sample-dcrwallet.conf`.


> Linux

1. Faça o download do arquivo correto:

    Para computadores 32-bit, faça o download do arquivo `decred-linux-386-v0.8.2.tar.gz` <br />
    Para computadores 64-bit, faça o download do arquivo `decred-linux-amd64-v0.8.2.tar.gz` <br />
    Para computadores 32-bit ARM, faça o download do arquivo `decred-linux-arm-v0.8.2.tar.gz` <br />
    Para computadores 64-bit ARM, faça o download do arquivo `decred-linux-arm64-v0.8.2.tar.gz`

2. Navegue até o local onde fez o download e extraia o arquivo .tar.gz:

    Gerenciador de arquivos do Ubuntu: clique com o botão direito no arquivo .tar.gz e clique em "Extrair aqui". <br />
    Terminal: utilize o comando `tar -xvzf filename.tar.gz`
    
    Os dois irão extrair o arquivo tar um uma pasta com o mesmo nome do arquivo. (`por exemplo tar -xvzf decred-linux-amd64-v0.8.2.tar.gz` deverá extrair para `decred-linux-amd64-v0.8.2`). A pasta deverá incluir `dcrctl`, `dcrd`, `dcrwallet`, `sample-dcrctl.conf`, `sample-dcrd.conf`, e `sample-dcrwallet.conf`.
    
> Windows

Observação: os Windows 7/8/10 oferecem suporte nativo para arquivos `.zip`, portanto é preferível utilizar o arquivo `.zip` assim não é necessário a instalação de um outro programa para o arquivo `.tar.gz`. As instruções são baseadas no arquivo `.zip`.

1. Faça o download do arquivo correto:

    Para computadores 32-bit, faça o download do arquivo `decred-windows-386-v0.8.2.zip`<br />
    Para computadores 64-bit, faça o download do arquivo `decred-windows-amd64-v0.8.2.zip`

2. Navegue até o local onde está o arquivo baixado e extraia o arquivo `.zip`:

    Gerenciador de arquivos: clique com o botão direito no arquivo .zip, selecione "Extrair tudo.." e uma janela irá se abrir perguntando qual pasta utilizar. O padrão irá extrair o arquivo `.zip` para uma pasta com o mesmo nome. Isso irá incluir os arquivos `dcrctl`, `dcrd`, `dcrwallet`, `sample-dcrctl.conf`, `sample-dcrd.conf`, e `sample-dcrwallet.conf`.

Se optar por baixar o arquivo `.tar.gz`, será necessário extrair o arquivo duas vezes e um software a parte (7-zip, winRAR, etc..) para conseguir os binários necessários.

---
