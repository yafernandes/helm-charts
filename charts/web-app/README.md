## Tested application servers

[Tomcat](https://tomcat.apache.org/)
```yaml
application:
  appServer:
    image: tomcat:9.0
    webappsDir: /usr/local/tomcat/webapps
    port: 8080
```

[Jetty](https://www.eclipse.org/jetty/)
```yaml
application:
  appServer:
    image: jetty:10-jre17-alpine
    webappsDir: /var/lib/jetty/webapps/
    port: 8080
```

[Open Liberty](https://openliberty.io/)
```yaml
application:
  appServer:
    image: websphere-liberty:webProfile8
    webappsDir: /config/dropins/
    port: 9080
```

[WildFly](https://www.wildfly.org/)
```yaml
application:
  appServer:
    image: quay.io/wildfly/wildfly:26.0.0.Final
    webappsDir: /opt/jboss/wildfly/standalone/deployments/
    port: 8080
```