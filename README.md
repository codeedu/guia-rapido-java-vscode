![Fullcycle](https://fullcycle.com.br/wp-content/themes/fullcycle-blog/application/img/logo-fullcycle.png)
# Guia rápido Java no VSCode
Neste guia rápido, aprenda como configurar o ambiente para trabalhar com projetos Java utilizando o VSCode e também WSL2 no Windows.

## O que é necessário?
- WSL2
- VSCode
- JDK

## O que é o WSL2 

Em 2016, a Microsoft anunciou a possibilidade de rodar o Linux dentro do Windows 10 como um subsistema e o nome a isto foi dado de **WSL** ou **Windows Subsystem for Linux**.

O acesso ao sistema de arquivos no Windows 10 pelo Linux era simples e rápido, porém não tinhamos uma execução completa do kernel do Linux, além de outros artefatos nativos e isto impossibilitava a execução de várias tarefas no Linux, uma delas é o Docker.

Em 2019, a Microsoft anunciou o **WSL 2**, com uma dinâmica aprimorada em relação a 1ª versão:

* Execução do kernel completo do Linux.
* Melhor desempenho para acesso aos arquivos dentro do Linux.
* Compatibilidade completa de chamada do sistema.

O WSL 2 já estava disponível na versão **Insider** do Windows 10, mas na última semana de maio de 2020 passou a estar disponível em final release na atualização **20.04** do Windows 10.

**Atualização**
A partir de 21 de agosto de 2020, o WSL 2 também está disponível nas edições 1903 e 1909, porém somente em sistemas x64.

Com WSL 2 é possível executar Docker no Linux usando o Windows 10.

Compare as versões: [https://docs.microsoft.com/pt-br/windows/wsl/compare-versions](https://docs.microsoft.com/pt-br/windows/wsl/compare-versions)

## O que é o VSCode
O Visual Studio Code (VSCode) é um editor de código-fonte leve, mas poderoso, que roda em sua área de trabalho e está disponível para Windows, macOS e Linux. 

Ele vem com suporte integrado para JavaScript, TypeScript e Node.js e tem um rico ecossistema de extensões para outras linguagens (como C ++, C #, Java, Python, PHP, Go) e tempos de execução (como .NET e Unity).

## O que é JDK
O Java Development Kit (JDK) é um conjunto de utilitários cuja a finalidade é permitir o desenvolvimento de softwares utilizando a plataforma Java. É um pacote disponibilizado pela Oracle, empresa detentora do Java. Acompanha todo ambiente necessário para a criação de aplicações Java.

## Instalação do WSL2
Para o passo a passo da instalação do WSL2 consulte o guia, [clicando aqui.](https://github.com/codeedu/wsl2-docker-quickstart/blob/master/README.md#instala%C3%A7%C3%A3o-do-wsl-2)

## Instalação VSCode
Começe acessando o site do VSCode <https://code.visualstudio.com/> clique em Download, você será redirecionado para a seguinte página:
![VSCode Download](https://i.imgur.com/EcP6K4L.png)
Selecione o sistema operacional Windows e clique no botão **Azul** logo abaixo da logo do Windows. Ao finalizar o download, execute o instalador e siga o passo a passo:
![1.Install VSCode](https://i.imgur.com/uM5yZpb.png)
Durante a instalação, será perguntado qual idioma deseja instalar. Avance todas as etapas do instalador até concluir a instalação e abra o Visual Studio Code.
## Instalação JDK
O processo de instalação da JDK, requer a instalação do WSL2. Certifique-se que você já possua o WSL2 instalado e configurado em sua maquina, após isso inicie o processo de instalação da JDK.

Abra o terminal do WSL2 ou Windows terminal, em seguida atualize todos os repositórios realizando o comando abaixo e pressionando a tecla **enter** é provável que ele peça para que você entre com a senha de administrador (root) caso aconteça, basta digitar a senha e pressionar a tecla **enter** novamente:
```
$ sudo apt update
```
![JDK Install](https://i.imgur.com/HE2uK9y.png)
Após finalizado o processo, chegou a hora de executar a instalação da JDK. Para isso é necessário a utilização do comando, digite e pressione a tecla **enter** e aguarde a finalização do processo:

```
$ sudo apt install default-jdk
```
![JDK 2 Install](https://i.imgur.com/0lwqxQw.png)
Pronto! A sua JDK já está instalada em seu WSL2. Agora é necessário efetuar a configuração do mesmo, criando a variável de ambiente ```JAVA_HOME``` e setando no ```PATH``` do seu sistema operacional.

Para verificar onde foi realizado a sua instalação, ainda em seu terminal, digite:

```
$ where java
```
![JDK 3 Install](https://i.imgur.com/fTdd21r.png)
Copie o caminho até antes de /bin e guarde ele com você. É possível que a versão esteja diferente da mostrada na imagem, não se preocupe, o Java sofre atualizações constantes mas o processo de instalação é igual para todas as versões.

```
/usr/lib/jvm/java-11-openjdk-amd64
```

Com o caminho em mãos, basta acessar o ```.bashrc``` ou caso utilize o oh-myzh o ```.zshrc``` atraves do comando:

Para .zshrc
```
$ nano .zshrc
```

Para .bashrc
```
$ nano .bashrc
```
Navegue até o final do arquivo e adicione uma nova linha contendo a configuração da variável de ambiente ```JAVA_HOME```:
```
### JAVA_HOME
export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
export PATH=$JAVA_HOME/bin:$PATH
```
![JDK 4 Install](https://i.imgur.com/KKSXPES.png)

Salve o arquivo, para isso, pressione **CTRL + X** e logo após **Y**. Reinicie o seu terminal, fechando e abrindo o mesmo novamente a após isso dê o comando:

```
$ java -version
```
![JDK 5 Install](https://i.imgur.com/p4UVelH.png)

Você deverá receber algo parecido com a imagem acima. Pronto! sua JDK já está funcionando. 
Verifique também se a configuração da sua variável ```JAVA_HOME``` foi realizar com sucesso, para isso basta executar o comando:

```
$ echo $JAVA_HOME
```
![JDK 6 Install](https://i.imgur.com/Der3WqF.png)

Caso receba algo parecido com a imagem, você conseguiu efetuar a instalação e também a configuração do JDK no seu WSL2.

## Configurando VSCode
Após o processo de instalação e configuração da JDK e do VSCode, é necessário instalar diversos plugins para que o ambiente de desenvolvimento Java utilizando o VSCode seja produtivo. 
Abra seu VSCode e navegue até a seção de extensões. Certifique-se que você está utilizando o WSL2 em seu VSCode para instalar as extensões.

![VSCode 7 Install](https://i.imgur.com/OmKmmPD.png)

Na seção de extensões, procure e instale as seguintes extensões:
- [Java Extension Pack](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-pack)
- [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode)
- [Project Manager for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-dependency)
- [Java Test Runner](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-test)
- [Debugger for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-debug)
- [Gradle Language Support](https://marketplace.visualstudio.com/items?itemName=naco-siren.gradle-language)
- [Gradle Tasks](https://marketplace.visualstudio.com/items?itemName=richardwillis.vscode-gradle)
- [Java Code Generators](https://marketplace.visualstudio.com/items?itemName=sohibe.java-generate-setters-getters) * foi separado do Java Extension Pack

Após o processo de instalação de todas as extensões acima, faça o restart do VSCode e a partir de agora estamos prontos para começar a trabalhar com Java utilizando VSCode. Basta abrir seu projeto Java no VSCode e começar a trabalhar!
