# O básico para iniciar

Este guia foi atualizado para a v0.8.2

---

Este guia se aplica para usuários de programas de linha de comando. Os usuários da Paymetheus e da Decrediton podem tranquilamente ignorar o uso dos config files - a Paymetheus e a Decrediton fazem a configuração básica automaticamente. É importante notar também que alguns de nossos guias mostram a configuração dos arquivos, enquanto outros mostram as command flags.

---

## Locais dos arquivos de configuração

Todo o software da Decred, quando inciado, verifica os arquivos de configuração para determinar quais configurações deverão ser ativadas/desativadas/ajustadas durante o carregamento inicial. Todas as startup flags de linha de comando`(e.g. dcrwallet --testnet)` podem ser substituídas por configurações dentro do arquivo de configuração apropriado `(e.g. dcrwallet --testnet could be replaced by testnet=1 in dcrwallet.conf)`.

Estes arquivos de configuração estão localizados na pasta home do respectivo software. A localização padrão das pastas para Windows, macOS/OSX, e Linux estão listadas abaixo:

Windows:

    C:\Users\<username>\AppData\Local\Dcrwallet\
    C:\Users\<username>\AppData\Local\Dcrd\
    C:\Users\<username>\AppData\Local\Dcrctl\ 
    C:\Users\<username>\AppData\Local\Decred\Paymetheus

macOS: 

    ~/Library/Application Support/Dcrwallet/
    ~/Library/Application Support/Dcrd/
    ~/Library/Application Support/Dcrctl/
    ~/Library/Application Support/decrediton/
    
Linux: 
    
    ~/.dcrwallet/
    ~/.dcrd/
    ~/.dcrctl/
    ~/.config/decrediton

Cada uma destas pastas possui seu próprio arquivo `.conf`, nomeado de acordo a sua aplicação (`por exemplo, dcrd utiliza dcrd.conf`). Note também que as pastas do `Dcrd` e da `Dcrwallet` são criadas automaticamente quando cada software é iniciado pelas primeira vez. Você terá que criar manualmente a pasta `Dcrctl` para utilizar o arquivo de configuração.

O método de instalação [dcrinstall](/getting-started/install-guide.md#dcrinstall) cria automaticamente os arquivos de configuração, com as [definições de configuração mínimas](#minimum-configuration) já habilitadas.

O método de instalação das [versões dos binários](/getting-started/install-guide.md#binary-releases) incluem os arquivos de configuração exemplo dentro do .zip/.tar.gz. É recomendável que você copie estes arquivos de configuração dentro da pasta recomendada, como descrito acima, e que os renomeie tirando o 'sample-'. Estes arquivos têm as configurações comentadas (os comentários não são lidos pelos programas durante a execução) assim todas estas configurações ficam desativadas. Você poderá habilitar estas configuração pré-escritas, simplesmente deletando o ponto-e-vírgula de antes da linha.

---

## Configuração mínima

No mínimo, para o `dcrd`, a `dcrwallet`, e o `dcrctl` serem capazes de comunicar entre si, eles terão que ser executados pela mesma combinação de rpcuser/rpcpass. Isto é feito automáticamente pelo método [dcrinstall](/getting-started/install-guide.md#dcrinstall). Para configuração manual, siga os passos abaixo:

1. Se as pastas listadas na seção [arquivos de configuração](#configuration-file-locations), não existirem nas dependencias do sistema operacional, você deverá criá-las para o `dcrd`, `dcrwallet`, e `dcrctl`.
2. Copie o [arquivo de configuração modelo](https://github.com/decred/dcrd/blob/master/sample-dcrd.conf) do Github, e cole em um novo arquivo de texto. Salve o arquivo texto como `dcrd.conf` na pasta `dcrd`.
3. Copie o [arquivo de configuração modelo](https://github.com/decred/dcrwallet/blob/master/sample-dcrwallet.conf) do Github, e cole em um novo arquivo de texto. Salve o arquivo texto como `dcrwallet.conf` na pasta `dcrwallet`.
4. Crie um arquivo de texto vazio e salve como `dcrctl.conf` na pasta `dcrctl`.
5. Crie um usuário e uma senha a sua escolha, que serão utilizados para a comunicação entre os softwares através de uma Chamada de Procedimento Remoto. A configuração mais simples é definir o mesmo para todos.
6. Dentro do `dcrd.conf`, sob `[Application Options]`, adicione as seguintes linhas:<br /><br />
        `rpcuser=<username-escolhido>`<br />
        `rpcpass=<password-escolhido>`<br /><br />
7. Dentro do `dcrwallet.conf`, sob `[Application Options]`, adicione as seguintes linhas:<br /><br />
        `username=<username-escolhido>`<br />
        `password=<password-escolhido>`<br /><br />
8. Dentro do `dcrctl.conf`, adicione as seguintes linhas:<br /><br />
        `rpcuser=<username-escolhido>`<br />
        `rpcpass=<password-escolhido>`<br /><br />
9. Salve os 3 arquivos.

---

## Startup Command Flags

A maioria das definições que você puder configurar pelo arquivo de configuração, poderão ser transmitidas para o software como parâmetro durante a inicialização. Por exemplo, os comandos específicos de cada sistema operacional (indicados abaixo), poderão abrir o `dcrd` para a Testnet, como alternativas para utilização de `testnet=1` no seu arquivo de configuração:

    Windows: dcrd.exe --testnet
    macOS: ./dcrd --testnet
    Linux: ./dcrd --testnet

O exemplo acima verificará primeiro o arquivo de configuração do `dcrd` para as definições e depois verificar o comando executável para habilitar a definição da testnet.

---

## Uso avançado

[Armazenando as informações de login nos arquivos de configuração](/advanced/storing-login-details.md) <!-- This has the same information found in the above, Minimum Configuration section. Could probably delete. -->

[Lista completa de comandos para cada aplicativo](/advanced/program-options.md)
