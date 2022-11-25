## Quick start

The default set of values deploys this [sammple application](https://github.com/yafernandes/datadog-experience/tree/main/learn-by-example/java-servlet) on a Tomcat 9. The default also relies on [automatic injection](https://docs.datadoghq.com/tracing/trace_collection/admission_controller/) of tracing library using the [Admission Controler](https://docs.datadoghq.com/containers/cluster_agent/admission_controller/?tab=helmchart).

```bash
helm repo add alexf https://yafernandes.github.io/helm-charts
helm install web-app alexf/web-app
```

If you want to just check the generated artifacts, without actually deploying anything, just use `template`, instead of `install`.

The *loadrunner* pod generates traffic to the deployed application.


[OpenTelemetry](https://opentelemetry.io/) can be selected by adding `--set datadog.instrumentation=otel`.

## Tested application servers

[Tomcat 9](https://tomcat.apache.org/) - **Default**
```yaml
application:
  appServer:
    image: tomcat:9.0
    webappsDir: /usr/local/tomcat/webapps
    port: 8080
```

[Tomcat 10](https://tomcat.apache.org/)
```yaml
application:
  appServer:
    image: tomcat:9.0
    webappsDir: /usr/local/tomcat/webapps
    port: 8080
  endpoints:
  - /servlet/servletAPI5
```

[Jetty 10](https://www.eclipse.org/jetty/)
```yaml
application:
  appServer:
    image: jetty:10-jre17-alpine
    webappsDir: /var/lib/jetty/webapps/
    port: 8080
```

[Jetty 11](https://www.eclipse.org/jetty/)
```yaml
application:
  appServer:
    image: jetty:11-jre17-alpine
    webappsDir: /var/lib/jetty/webapps/
    port: 8080
  endpoints:
  - /servlet/servletAPI5
```

[Open Liberty](https://openliberty.io/)
```yaml
application:
  appServer:
    image: websphere-liberty:webProfile8
    webappsDir: /config/dropins/
    port: 9080
```

[WildFly 26](https://www.wildfly.org/)
```yaml
application:
  appServer:
    image: quay.io/wildfly/wildfly:26.0.0.Final
    webappsDir: /opt/jboss/wildfly/standalone/deployments/
    port: 8080
```

[WildFly 27](https://www.wildfly.org/)
```yaml
application:
  appServer:
    image: quay.io/wildfly/wildfly:27.0.0.Final-jdk19
    webappsDir: /opt/jboss/wildfly/standalone/deployments/
    port: 8080
  endpoints:
  - /servlet/servletAPI5
```