# SpringJWT

Spring Web
Spring OAuth2 Resource Server
Spring Configuration Processor

Version 1
InMemoryUserDetailsManager
httpBasic

Version 2
OAuth2 - JWT 

#Generate Private/Public Keys
Terminal - cd src/main/resources/certs - Run

#keypair.pem is the private key.
openssl genrsa -out keypair.pem 2048

#public.pem is the public key.
openssl rsa -in keypair.pem -pubout -out public.pem

#private key need to be pkcs8 encoded
openssl pkcs8 -topk8 -inform PEM -outform PEM -nocrypt -in keypair.pem -out private.pem
#Delete keypair.pem

@ConfigurationProperties need @EnableConfigurationProperties(RsaKeyProperties.class) before public class SpringJwtApplication {}

Run Build first to let properties shown in application.properties

JWTDecoder, JWTEncoder

#Test Method 1 - Postman
1. GET - http://localhost:8080 -> 401 Unauthorized
2. New Tab - POST - Authorization Type: Basic Auth - Username/Password - http://localhost:8080/token - Send
3. Copy Token - Back to 1. - Authorization Type: Bearer Token - Paste Token from 2. - Send

#Test Method 2 - Httpie - Skipped
