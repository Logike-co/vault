keytool -genkeypair -alias bco -keyalg RSA -keysize 2048 -keystore bco.jks -validity 3650

keytool -genkeypair -alias bco -keyalg RSA -keysize 2048 -storetype PKCS12 -keystore bco.p12 -validity 3650 -ext san=dns:localhost

keytool -export -keystore local-ssl.p12 -alias local_ssl -file local-cert.crt