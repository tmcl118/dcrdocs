# **Diferenças das linhas de comando entre os Sistemas Operacionais**

Esta página foi atualizada para a v0.8.2.

O objetivo desta página é explicar as principais diferenças ao executar os aplicativos multi-plataforma para Windows, Linux e macOS/OSX, utilizando linha de comando.

> Comandos de inicialização

A primeira grande diferença dos aplicativos de linha de comando (`dcrd`,) é como inicializá-los.  Estas diferenças não são exatamente relacionadas ao sistema operacional, mas sim em relação aos shells. Windows vem com o Prompt de Comando e o PowerShell instalado. O macOS utiliza Bash dentro do aplicativo Terminal, e muitas distribuições Linux utilizam Bash também. Abaixo estão os exemplos dos comandos básico para executar, para Bash e para Prompt de Comando.

**Prompt de Comando:** `dcrd.exe`, `dcrwallet.exe`, `dcrctl.exe` <br />
**Bash:** `./dcrd`, `./dcrwallet`, `./dcrctl`

Muitos de nossos guias não utilizarão nenhum sistema operacional como base para os comando. Assim, se o guia disse para executar o comando `dcrctl --wallet getbalance`, você deverá utilizar `dcrctl.exe --wallet getbalance` para o Prompt de Comando e `./dcrctl --wallet getbalance` para o Bash.

> Local da pasta de programas

Outro item que é diferente em relação aos sistemas operacionais, é o local onde os programas ficam instalados (blocos, carteiras e arquivos de configuração são todos armazenados na pasta de programas). Abaixo você encontra uma tabela com as pastas de programas padrão de cada sistema operacional.

| OS      | Pasta dos programas dcrd, dcrwallet, dcrctl      | 
| -------:|:--------------------------------------------- |
| Windows | `C:\Users\<your-username>\AppData\Local\dcrd\`      |
|         | `C:\Users\<your-username>\AppData\Local\dcrwallet\` | 
|         | `C:\Users\<your-username>\AppData\Local\dcrctl\`    |
| macOS   | `~/Library/Application Support/dcrd/`         |
|         | `~/Library/Application Support/dcrwallet/`    |
|         | `~/Library/Application Support/dcrctl/`       |
| Linux   | `~/.dcrd/`                                    |
|         | `~/.dcrwallet/`                               |
|         | `~/.dcrctl/`                                  |

