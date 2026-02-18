
``` yaml
# Compose file for keycloak development environment.
# 
# @author <a href="mailto:javier.latorre@logike.co">Javier Latorre</a>
# @profile localhost
# @version 1.0 08-02-2026
services:
  keycloak-db:
    image: postgres:14
    command: -p 5439
    container_name: keycloak-db
    environment:
	    POSTGRES_USER: ${POSTGRES_USER}
	    POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
	    POSTGRES_DB: keycloak
    expose:
      - "5439"
    volumes:
      - ./volumes/keycloak-db:/var/lib/postgresql/data
    ports:
      - "5439:5439"
    restart: always

  keycloak:
    image: quay.io/keycloak/keycloak:latest
    command: start-dev
    container_name: keycloak
    ports:
	    - "8443:8443"
	    - "8090:8080"
    environment:
	    KEYCLOAK_ADMIN: ${KEYCLOAK_USER}
	    KEYCLOAK_ADMIN_PASSWORD: ${KEYCLOAK_PASSWORD}
	    KC_HOSTNAME: ${KEYCLOAK_URL}
	    KC_DB_URL: jdbc:postgresql://keycloak-db:5439/keycloak
	    KC_DB: postgres
	    KC_DB_USERNAME: ${POSTGRES_USER}
	    KC_DB_PASSWORD: ${POSTGRES_PASSWORD}
    depends_on:
      - keycloak-db

volumes:
  keycloak-db:
```

.env
``` yaml
KEYCLOAK_USER=admin
KEYCLOAK_PASSWORD=admin123
KEYCLOAK_URL=localhost
POSTGRES_USER=postgres
POSTGRES_PASSWORD=pgpass
```

https://github.com/Tauromachian/keycloak-production-docker-compose/blob/master/docker-compose.dev.yml

https://www.keycloak.org/getting-started/getting-started-docker
https://www.keycloak.org/ui-customization/themes
https://www.baeldung.com/keycloak-custom-login-page

https://reducto.ai/

https://www.keycloak.org/
https://www.keycloak.org/guides#server
https://vaadin.com/docs/latest/tools/sso/integrations/keycloak
https://martinelli.ch/vaadin-oauth2-and-keycloak/
https://vaadin.com/forum/t/vaadin-24-and-keycloak-integration/167544
https://dev.to/aissam_assouik/integration-vaadin-oauth2-authentication-with-keycloak-194f
https://foojay.io/today/vaadin-oauth2-and-keycloak/

## Open Source Identity and Access Management

https://www.youtube.com/watch?v=La082JsJoH4
https://github.com/vaadin/vaadin-sso-kit-keycloak-demo
https://vaadin.com/docs/latest/tools/sso/integrations/keycloak
https://www.keycloak.org/

https://github.com/vaadin/flow-crm-tutorial/blob/v24/src/main/java/com/example/application/security/SecurityService.java

https://github.com/vaadin/bookstore-example/blob/v24/src/main/java/org/vaadin/example/bookstore/ui/login/LoginScreen.java
https://github.com/vaadin/vaadin-form-example/blob/v24/src/main/java/org/vaadin/examples/form/ui/MainView.java
https://github.com/vaadin/archetype-application-example/blob/master/mockapp-ui/src/main/java/org/vaadin/mockapp/samples/authentication/AccessControl.java

https://stackoverflow.com/questions/74280877/vaadin-23-spring-security-with-keycloak-redirect-user-after-login-to-the-corre

https://martinelli.ch/vaadin-oauth2-and-keycloak/

https://github.com/simasch/vaadin-keycloak/blob/main/src/main/java/ch/martinelli/demo/keycloak/views/user/UserView.java

https://vaadin.com/docs/latest/tools/sso/integrations/keycloak

https://www.youtube.com/watch?v=_MxRmGTkDgo&ab_channel=vaadinofficial

https://www.youtube.com/watch?v=La082JsJoH4&ab_channel=JavaTechie

https://www.youtube.com/watch?v=Kg6loeM3tVE&ab_channel=CodingTogetherES

https://www.youtube.com/watch?v=bxy2JgqqKDU&ab_channel=vaadinofficial

https://www.youtube.com/watch?v=dZuy1v9isXE&ab_channel=vaadinofficial

https://docs.spring.io/spring-security/reference/servlet/authentication/passwords/jdbc.html#servlet-authentication-jdbc-bean

https://github.com/peholmst/spring-security-webinar-2021/blob/main/src/main/java/org/vaadin/webinar/security/sampleapp/SampleAppApplication.java

https://vaadin.com/docs/latest/security/enabling-security

https://www.tutorialspoint.com/spring_boot/spring_boot_eureka_server.htm

MCP SERVER
https://shaaf.dev/post/2026-01-02-keycloak-mcp-server/?ref=dailydev