(Imagem legal aqui)

---

# Índice

- [Índice](#%C3%ADndice)
- [Introdução](#introdu%C3%A7%C3%A3o)
- [Requisitos](#requisitos)
  - [STM32 Cube MX](#stm32-cube-mx)
    - [Instalção no Windows](#instal%C3%A7%C3%A3o-no-windows)
    - [Instalação no Linux](#instala%C3%A7%C3%A3o-no-linux)
  - [arm-none-eabi-gcc](#arm-none-eabi-gcc)
    - [Instalação no Windows](#instala%C3%A7%C3%A3o-no-windows)
    - [Instalação no Linux](#instala%C3%A7%C3%A3o-no-linux-1)
  - [Make](#make)
    - [Instalação no Windows](#instala%C3%A7%C3%A3o-no-windows-1)
    - [Instalação no Linux](#instala%C3%A7%C3%A3o-no-linux-2)
  - [Git](#git)
    - [Instalação no Windows](#instala%C3%A7%C3%A3o-no-windows-2)
    - [Instalação no Linux](#instala%C3%A7%C3%A3o-no-linux-3)

---

# Introdução

Este documento tem como objetivo explicar como é feita a programação de
microcontroladores da STMicroelectronics, voltado especialmente para os
robôs da equipe ThundeRatz que usam placas com esses microcontroladores.

Nas próximas seções serão apresentados os softwares necessários para
isso, e uma explicação de como programar algumas das principais
funcionalidades desses microcontroladores.

# Requisitos

Para poder escrever programas para os microcontroladores da ST é
necessário baixar alguns softwares e bibliotecas específicas, bem como um
editor de texto.

## STM32 Cube MX

Esse software é bem importante quando se está no começo do
desenvolvimento e é utilizado desde o projeto de placa. Nele, é possível
setar várias configurações de pinos e periféricos por meio de uma
interface gráfica e gerar o código disso automaticamente, o que seria
muito difícil de fazer na mão.

Para baixá-lo, acesse [este link](http://www.st.com/en/development-tools/stm32cubemx.html).

Instruções gerais de uso se encontram logo na próxima seção. Instruções
específicas estarão em suas respectivas seções.

### Instalção no Windows

Extraia o .zip e execute o arquivo SetupSTM32CubeMX-X.X.X.exe (X.X.X é a
versão). Siga as instruções da tela.

É necessário colocar o local de instalação em uma nova variável de ambiente
chamada `CUBE_PATH`. O local de instalação padrão é `C:\Program Files (x86)\STMicroelectronics\STM32Cube\STM32CubeMX`.

IMAGEM AQUI

### Instalação no Linux

É necessário instalar Java. Para isso, execute os seguintes comandos:

```bash
$ sudo add-apt-repository ppa:linuxuprising/java
$ sudo apt update
$ sudo apt install oracle-java10-installer
```

Agora, execute o arquivo SetupSTM32CubeMX-X.X.X.linux. Substitua X.X.X pela
versão baixada.

```bash
$ sudo ./SetupSTM32CubeMX-X.X.X.linux
```

Siga as instruções na tela.

É possível que ocorra alguns erros porque o Cube depende de bibliotecas de
sistemas de 32 bits. Instale a biblioteca libc6-i386 para resolver o
problema:

```bash
$ sudo apt install libc6-i386
```

Tente executar o arquivo novamente.

Após a instalação, crie uma variável chamada CUBE_PATH com o local de
instalação do Cube nas configurações da shell que você utiliza. Na pasta
deve conter o executável STM32CubeMX. O procedimento é similar a adicionar
diretórios no PATH (Apêndice 2), mas com o nome da variável diferente e sem
adicionar ao valor anterior da variável.

O local de instalação padrão é `/usr/local/STMicroelectronics/STM32Cube/STM32CubeMX`.

Muito bem! O Cube foi instalado com sucesso. Porém, ao olhar no menu de
programas, pode-se perceber que ele não aparece em lugar nenhum. Para isso,
é necessário criar uma entrada para ele dentro do menu. Faça isso com:

```bash
$ cd /usr/share/applications
$ sudo gedit stm32cubemx.desktop
```

Dentro do arquivo em branco criado, digite:

```conf
[Desktop Entry]
Name=STM32 Cube MX
GenericName=STM32 Cube MX
Comment=STM32 Cube initialization code generator
Exec=/seu/local/de/instalacao/STM32CubeMX
Icon=/seu/local/de/instalacao/help/STM32CubeMX.ico
Terminal=false
Type=Application
Categories=Development;Electronics;
```

## arm-none-eabi-gcc

Esse é o compilador de C para ARM e é necessário tê-lo para compilar os
programas. Para baixá-lo, acesse [esse link](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads).

### Instalação no Windows

Baixe a versão mais recente para seu sistema e execute o instalador.

<!-- LINK AQUI -->

Após a instalação, coloque o local dos executáveis no Path (Apêndice 2). O
local padrão no Windows é `C:\Program Files (x86)\GNU Tools Arm Embedded\7 2018-q2-update\bin`.

### Instalação no Linux

Baixe o arquivo `.tar.bz2` e extraia usando o comando:

```bash
$ tar xjvf gcc-arm-none-eabi-*.tar.bz2
```

Mova a pasta gerada para qualquer lugar que desejar.

<!-- LINK AQUI -->

Após a instalação é necessário colocar os executáveis no PATH (Apêndice 2).
Eles estão na pasta bin, dentro da pasta extraída.

## Make

Para poder compilar com mais facilidade, é necessário ter o make instalado.

### Instalação no Windows

<!-- LINK AQUI -->

Baixe pelo MSYS2 (Apêndice 3).

### Instalação no Linux

Instale pelo gerenciador de pacotes. No caso do Ubuntu:

```bash
$ sudo apt install make
```

## Git

Para pegar o STM32 Project Template e fazer o controle de versão.

### Instalação no Windows

Para baixar acesse [esse link](https://git-scm.com/downloads).

Execute o instalador. Deixe as opções padrões, assim o local de instalação
já será adicionado ao Path.

### Instalação no Linux

Instale pelo gerenciador de pacotes. No caso do Ubuntu:

```bash
$ sudo apt install git
```
