## Quick start

The default set of values deploys [this](https://github.com/yafernandes/datadog-experience/tree/main/learn-by-example/java-servlet) sample application on a Tomcat 9. The default also relies on [automatic injection](https://docs.datadoghq.com/tracing/trace_collection/admission_controller/) of tracing library using the [Admission Controler](https://docs.datadoghq.com/containers/cluster_agent/admission_controller/?tab=helmchart).

```bash
helm repo add alexf https://yafernandes.github.io/helm-charts
helm install web-app alexf/web-app
```

## Tested application servers

[Tomcat](https://tomcat.apache.org/) - **Default**
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