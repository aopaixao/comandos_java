## Lista de comandos e instruções JAVA

Lista de comandos e instruções Java.

## Índice
<!--ts-->
   * [Configurações para Debug no Eclipse/STS](#configuracoes_debug)
   * [Utilização de Certificados HTTPS nos serviços REST e SOAP](#intrucoes-rest-soap)
      * [Configuração do Arquivo CACERTS](#configuracao-cacerts)
      * [Importação de Certificados para o CACERTS](#importacao-certificados-cacerts)
      * [Listagem de Certificados Importados](#listagem-certificados-importados)
      * [Sobre - Licença - Autor](#sobre)
<!--te-->

<a id="configuracoes_debug"></a>
### Configurações para Debug no Eclipse/Spring Tools Suite de aplicações que fazem conexão remota

A configuração abaixo habilita a exibição de logs estendidos no console, onde é possível visualizar várias informações relativas ao consumo de recursos remotos.

```bash
# Acesse o menu RUN ou Debug Configurations e acesse a aba Arguments. Insira a linha abaixo em VM arguments
$ -Djavax.net.debug=ALL:handshake;-Dhttps.protocols=TLSv1.3;--ilegal-access=deny
```
Além das opções utilizadas acima, há várias outras disponíveis. Consulte a documentação oficial.

<a id="intrucoes-rest-soap"></a>
### Utilização de Certificados HTTPS nos serviços REST e SOAP

<a id="configuracao-cacerts"></a>
#### Configuração do Arquivo CACERTS

1. Para utilização/consumo de serviços REST ou SOAP é necessário importar o certificado digital relativo ao domínio dos serviços para o arquivo "cacerts"
2. O arquivo "cacerts" padrão do projeto ficará hospedado em uma pasta no sistema de arquivos e seu caminho estará contido nos arquivos de propriedades
    1. O caminho padrão no servidor de aplicação para hospedagem do arquivo "cacerts" é /opt/gs_files/certificados
    2. O desenvolvedor poderá baixar o arquivo "cacerts" do servidor onde a aplicação está hospedada e armazená-lo localmente
    3. Ao utilizar o certificado localmente, será necessário modificar o seu caminho no arquivo de propriedades, tomando-se o cuidado de não commitar tal mudança quando atualizar o projeto

<a id="importacao-certificados-cacerts"></a>
#### Importação de Certificados para o CACERTS
A importação de um novo certificado para utilização no projeto deverá seguir os passos abaixo.

1. Acessar a URL do serviço através do navegador Web (recomenda-se o Google Chrome)
2. Clicar, na barra de endereço do navegador, no ícone (cadeado) do certificado 
3. No pop-up, clicar em "Certificado"
4. Na janela aberta, clicar na aba "Detalhes"
    1. Estando na aba "Detalhes", clicar em "Copiar para Arquivo..."
    2. Na tela do "Assistente para Exportação de Certificados", clicar em "Avançar"
    3. Nas opções de formato a ser usado, escolher "X.509 binário codificado por DER (*.cer)
    4. Definir o lugar onde será salvo o certificado com a extensão ".cer". Recomenda-se utilizar o nome do serviço como nome do arquivo contendo o certificado
5. Após ter salvado o certificado, inicie o prompt do DOS com privilégio de Administrador
    1. Estando no prompt, acesse a pasta JAVA_HOME/bin
    2. Execute o seguinte comando: keytool -importcert -trustcacerts -file "CAMINHO_COMPLETO_CERTIFICADO_EXPORTADO_COM_EXTENSAO_CER" -alias ALIAS_DO_CERTIFICADO -keystore "CAMINHO_COMPLETO_ARQUIVO_CACERTS"
        1. CAMINHO_COMPLETO_CERTIFICADO_EXPORTADO_COM_EXTENSAO_CER : substitua pelo caminho do sistema de arquivos onde o certificado foi armazenado
        2. ALIAS_DO_CERTIFICADO: substitua pelo alias do certificado. Recomenda-se utilizar o domínio/URL do serviço. Ex.: dminerweb.com.br
        3. CAMINHO_COMPLETO_ARQUIVO_CACERTS: substitua pelo caminho do sistema de arquivos onde o arquivo "cacerts" do projeto foi armezenado
    3. A senha padrão do arquivo "cacerts" é changeit
    4. Quando questionado sobre confirmar no arquivo que está sendo importado, digite y (ou sim) e tecle "enter"
    5. Ao final do processo será exibida uma mensagem de sucesso. Caso contrário, reveja os passos acima ou contate outro desenvolvedor/líder técnico do projeto/arquiteto Neki.

<a id="sobre"></a>
## Sobre

- Author - [Alexandre Paixão]

## Licença

GNU GPL
