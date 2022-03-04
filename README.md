## Lista de comandos e instruções JAVA

Lista de comandos e instruções Java.

### Configurações para Debug no Eclipse/Spring Tools Suite de aplicações que fazem conexão remota

A configuração abaixo habilita a exibição de logs estendidos no console, onde é possível visualizar várias informações relativas ao consumo de recursos remotos.

```bash
# Acesse o menu RUN ou Debug Configurations e acesse a aba Arguments. Insira a linha abaixo em VM arguments
$ -Djavax.net.debug=ALL:handshake;-Dhttps.protocols=TLSv1.3;--ilegal-access=deny
```
Além das opções utilizadas acima, há várias outras disponíveis. Consulte a documentação oficial.


## Sobre

- Author - [Alexandre Paixão]

## Licença

GNU GPL
