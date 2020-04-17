
# HTTPS com TLS

Linha de comando para geração do pacote JKS, preenchendo o CN=localhost.

```
keytool -genkeypair -keystore self.jks -keyalg rsa -alias self
```

Copiar o pacote JKS para o diretório `src/main/resources`
(certificar-se que está visível no Anypoint Studio).

Configurar o conector `HTTP Listener` para usar o protocolo `HTTPS` na porta 8082.

