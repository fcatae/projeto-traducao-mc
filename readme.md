
# HTTPS com TLS

Linha de comando para geração do pacote JKS, preenchendo o CN=localhost.

```
keytool -genkeypair -keystore self.jks -keyalg rsa -alias self
```

Copiar o pacote JKS para o diretório `src/main/resources`
(certificar-se que está visível no Anypoint Studio).

Configurar o conector `HTTP Listener` para usar o protocolo `HTTPS` na porta 8082.

# Fazer chamadas HTTP com OAuth (client credentials)

Adicionar o módulo OAuth nas ferramentas.

```xml
<dependency>
    <groupId>org.mule.modules</groupId>
    <artifactId>mule-oauth-module</artifactId>
    <version>1.1.11</version>
    <classifier>mule-plugin</classifier>
</dependency>
```

Configurar a autenticação Client Credentials no HTTP Request.


# Adicionar implementação Java

Criar o arquivo `LimpaCaracter.java` no diretório `src/main/java` contendo uma
classe estática pública. Por exemplo:

```java
public class LimpaCaracter {
	public static String limpar(String texto) {
		return "Ola Jose";
	}
}
```

Referenciar esse arquivo no Data Weave usando o `import`.

```dw
%dw 2.0
output application/json
import java!LimpaCaracter
---
{
	entrada: vars.str,
	saida: java!LimpaCaracter::limpar(vars.str) 
}
```

