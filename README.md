<h1 align="center">
  <br>
  <a href="#"><img src="./java-monitor-de-carga/projeto1/icon2.png" alt="Monitor de Carga" width="200"></a>
  <br>
  Monitor de carga - Java
  <br>
</h1>

<h4 align="center">Leitor Serial para uso em conjuto com sistema Arduino usando Java.</h4>

<p align="center">
  <a href="#Características">Características</a> •
  <a href="#Como Usar">Como usar</a> •
  <a href="#Download / Clone">Download / Clone</a> •
  <a href="#Creditos">Creditos</a> •
</p>
<p align="center" >
    <img src="./java-monitor-de-carga/projeto1/anima.gif" alt="Monitor de Carga">
</p >

## Características

* Seletor Porta Com
  - Veja no menu dropdown as portas disponiveis no computador e seu fabricante.
* Recebe e exibe o status de carga
  - Enquanto carrega, o sistema envia os dados e o monitor os recebe e exibe.
* Recebe e exibe as configuraçõe do modo de carga
  - Exibe os parâmetros chave do modo atual.
* Mantêm o fluxo de dados da serial ativo e de forma automática
* Barra de status de carga animada
* Compatível com sistemas que utilizam protocolo UART (Ex.: Arduino) 
* Cross platform ready - Java JVM
  - Atraves da JVM é possivel rodar em sistemas Windows, Linux e Mac

## Como usar

Para usar esta aplicação é necessário obedecer ao padrão de transmissão abaixo. Uma vez que o sistema alvo esteja enviando os dados, o Monitor de carga irá receber e processar. Para ter um guia de sistema que utiliza o recurso veja o Sistema MUF800R00 [Github](https://github.com/marcostech/Projetos_Sistemas_Embarcados). 
Este padrão de transmissão foi escrito na linguagem utilizada na plataforma Arduino, portanto pode ser usado em seu projeto sem a adição de outras bibliotecas.
O baudrate do sistema deve ser 115200.

```c
// Todo pacote de dados deve ser enviado desta forma, obedecendo a 
// separação por CSV ',' e por delimitadores de inico e fim de transmissão.
// inico do pacote 
// '<'
// ...
// 'Pacote'
// ...
// '>'
// 'new Line char'
// fim do pacote
    Serial.begin(115200); //Manter este baudrate
    Serial.print(F("<"));  
    Serial.print(F(","));
    Serial.print(F("V: "));
    Serial.print(/* Sua tensão de bateria */);  
    Serial.print(F(","));
    Serial.print(F("T: "));
    Serial.print(/* Seu tempo atual */);  
    Serial.print(F(","));
    Serial.print(F("C: "));
    Serial.print(/* Seu ciclo atual */);  
    Serial.print(F(","));
    Serial.print(F("S: "));
    Serial.print(/* Seu estado atual */);  
    Serial.print(F(","));
    Serial.print(F("CFG1: "));
    Serial.print(/* Sua configuração de tensão minima */);  
    Serial.print(F(","));
    Serial.print(F("CFG2: "));
    Serial.print(/* Sua configuração de tensão máxima */);  
    Serial.print(F(","));
    Serial.print(F("CFG3: "));
    Serial.print(/* Sua configuração de tempo máximo */);  
    Serial.print(F(","));
    Serial.print(F("CFG4: "));
    Serial.print(/* Sua configuração de modo atual */);  
    Serial.print(F(","));
    Serial.print(F(">"));
    Serial.println();
```

> **Nota**
> Se você não estiver usando estas funções para envio de dados na porta Serial basta enviar os dados conforme está descrito no exemplo (<,...Pacote1,Pacote2,...,>'newLineChar'), prestando atenção no 'new Line char' que só deve ser enviado ao final.


## Download / Clone

Você pode fazer o clone do projeto e então sua build para a plataforma alvo ou se preferir pode baixar o arquivo .jar e rodar direto em sua máquina!

## Creditos

Esse Software utiliza os pacotes Open Source abaixo:

- [jSerialCom](https://github.com/Fazecast/jSerialComm)
- [Arduino](https://www.arduino.cc/)