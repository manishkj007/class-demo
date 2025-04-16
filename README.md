I0416 10:13:17.064409       1 version.go:31] "version info" version="" commit="647b715" buildDate="2023-11-12T21:36:52Z" component="vaultenv"
I0416 10:13:17.064508       1 main.go:184] "azure key vault env injector initializing"
I0416 10:13:17.064769       1 main.go:253] "found original container command" cmd="/bin/sh" args=["/bin/sh","-c","java $JAVA_OPTS -jar r2d2-qiss-1.0.0.jar"]
I0416 10:13:17.064822       1 authentication.go:110] "checking if current auth service credentials are stale" url="http://akv2k8s-akv2k8s-envinjector.akv2k8s.svc:80/auth/ns-gwam-r2d2-uat/gwam-pumkt-r2d2-dp-7dfd9b7bf6-fdfqn?secret=akv2k8s-gwam-pumkt-r2d2-dp"
I0416 10:13:17.292114       1 authentication.go:123] "auth service credentials ok" url="http://akv2k8s-akv2k8s-envinjector.akv2k8s.svc:80/auth/ns-gwam-r2d2-uat/gwam-pumkt-r2d2-dp-7dfd9b7bf6-fdfqn?secret=akv2k8s-gwam-pumkt-r2d2-dp"
I0416 10:13:17.292423       1 authentication.go:159] "requesting azure key vault oauth token" url="https://akv2k8s-akv2k8s-envinjector.akv2k8s.svc:9443/auth/ns-gwam-r2d2-uat/gwam-pumkt-r2d2-dp-7dfd9b7bf6-fdfqn"
I0416 10:13:17.318418       1 authentication.go:179] "successfully received oauth token"
I0416 10:13:17.468457       1 main.go:338] "secret injected into env var" azurekeyvaultsecret="ns-gwam-r2d2-uat/iddl-qa-key" env="IDDL_QA_KEY"
I0416 10:13:17.528527       1 main.go:338] "secret injected into env var" azurekeyvaultsecret="ns-gwam-r2d2-uat/sql-database" env="SQL_DATABASE"
I0416 10:13:17.571696       1 main.go:338] "secret injected into env var" azurekeyvaultsecret="ns-gwam-r2d2-uat/sql-pwd" env="SQL_PWD"
I0416 10:13:17.628521       1 main.go:338] "secret injected into env var" azurekeyvaultsecret="ns-gwam-r2d2-uat/sql-id" env="SQL_ID"
I0416 10:13:17.666076       1 main.go:338] "secret injected into env var" azurekeyvaultsecret="ns-gwam-r2d2-uat/jwt-key" env="JWT_KEY"
I0416 10:13:17.707740       1 main.go:338] "secret injected into env var" azurekeyvaultsecret="ns-gwam-r2d2-uat/qiss-key" env="QISS_KEY"
I0416 10:13:17.820170       1 main.go:338] "secret injected into env var" azurekeyvaultsecret="ns-gwam-r2d2-uat/sql-server" env="SQL_SERVER"
I0416 10:13:17.820201       1 main.go:343] "starting process with secrets in env vars" cmd="/bin/sh" args=["/bin/sh","-c","java $JAVA_OPTS -jar r2d2-qiss-1.0.0.jar"]
2025-04-16T10:13:18,869-0400 [16 1] com.newrelic INFO: New Relic Agent: Loading configuration file "/var/newrelic/./newrelic.yml"
2025-04-16T10:13:18,972-0400 [16 1] com.newrelic INFO: Using default collector host: collector.newrelic.com
2025-04-16T10:13:18,972-0400 [16 1] com.newrelic INFO: Using default metric ingest URI: https://metric-api.newrelic.com/metric/v1
2025-04-16T10:13:18,972-0400 [16 1] com.newrelic INFO: Using default event ingest URI: https://insights-collector.newrelic.com/v1/accounts/events
2025-04-16T10:13:19,197-0400 [16 1] com.newrelic INFO: New Relic Agent: Writing to log file: /var/newrelic/logs/newrelic_agent.log

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::                (v3.2.4)

2025-04-16T10:13:30.837-04:00  INFO 16 --- [           main] com.r2d2.qiss.R2D2QissApplication        : Starting R2D2QissApplication v1.0.0 using Java 17 with PID 16 (/usr/local/bin/r2d2-qiss-1.0.0.jar started by gwam in /usr/local/bin)
2025-04-16T10:13:30.857-04:00  INFO 16 --- [           main] com.r2d2.qiss.R2D2QissApplication        : The following 1 profile is active: "uat"
2025-04-16T10:13:36.543-04:00  INFO 16 --- [           main] .s.d.r.c.RepositoryConfigurationDelegate : Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2025-04-16T10:13:37.449-04:00  INFO 16 --- [           main] .s.d.r.c.RepositoryConfigurationDelegate : Finished Spring Data repository scanning in 893 ms. Found 12 JPA repository interfaces.
2025-04-16T10:13:39.363-04:00  INFO 16 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port 8080 (http)
2025-04-16T10:13:39.557-04:00  INFO 16 --- [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2025-04-16T10:13:39.558-04:00  INFO 16 --- [           main] o.apache.catalina.core.StandardEngine    : Starting Servlet engine: [Apache Tomcat/10.1.19]
2025-04-16T10:13:39.742-04:00  INFO 16 --- [           main] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2025-04-16T10:13:39.743-04:00  INFO 16 --- [           main] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 8389 ms
2025-04-16T10:13:40.383-04:00  INFO 16 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2025-04-16T10:13:50.860-04:00  WARN 16 --- [           main] c.m.s.j.internals.SQLServerConnection    : ConnectionID:1 ClientConnectionId: e7083272-e021-42d6-aee5-6d9117375bc0 Prelogin error: host gwam-dl-mim-uat-cac-sqlmi-qdb.5cc6f8808a35.database.windows.net port 1433 Error reading prelogin response: Connection reset ClientConnectionId:e7083272-e021-42d6-aee5-6d9117375bc0
2025-04-16T10:14:00.966-04:00  WARN 16 --- [           main] c.m.s.j.internals.SQLServerConnection    : ConnectionID:1 ClientConnectionId: b437daa0-bea0-4c42-80d1-24d676391230 Prelogin error: host gwam-dl-mim-uat-cac-sqlmi-qdb.5cc6f8808a35.database.windows.net port 1433 Error reading prelogin response: Connection reset ClientConnectionId:b437daa0-bea0-4c42-80d1-24d676391230
2025-04-16T10:14:11.170-04:00  WARN 16 --- [           main] c.m.s.j.internals.SQLServerConnection    : ConnectionID:1 ClientConnectionId: 5e07dbdc-6ae1-4a00-a151-a1cf4dfddd34 Prelogin error: host gwam-dl-mim-uat-cac-sqlmi-qdb.5cc6f8808a35.database.windows.net port 1433 Error reading prelogin response: Connection reset ClientConnectionId:5e07dbdc-6ae1-4a00-a151-a1cf4dfddd34
2025-04-16T10:14:12.179-04:00 ERROR 16 --- [           main] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Exception during pool initialization.

com.microsoft.sqlserver.jdbc.SQLServerException: Connection reset ClientConnectionId:5e07dbdc-6ae1-4a00-a151-a1cf4dfddd34
	at com.microsoft.sqlserver.jdbc.SQLServerConnection.terminate(SQLServerConnection.java:4026) ~[mssql-jdbc-12.4.2.jre11.jar!/:na]
	at com.microsoft.sqlserver.jdbc.TDSChannel.read(IOBuffer.java:2166) ~[mssql-jdbc-12.4.2.jre11.jar!/:na]
	at com.microsoft.sqlserver.jdbc.SQLServerConnection.prelogin(SQLServerConnection.java:3736) ~[mssql-jdbc-12.4.2.jre11.jar!/:na]
	at com.microsoft.sqlserver.jdbc.SQLServerConnection.connectHelper(SQLServerConnection.java:3548) ~[mssql-jdbc-12.4.2.jre11.jar!/:na]
	at com.microsoft.sqlserver.jdbc.SQLServerConnection.login(SQLServerConnection.java:3172) ~[mssql-jdbc-12.4.2.jre11.jar!/:na]
	at com.microsoft.sqlserver.jdbc.SQLServerConnection.connectInternal(SQLServerConnection.java:3014) ~[mssql-jdbc-12.4.2.jre11.jar!/:na]
	at com.microsoft.sqlserver.jdbc.SQLServerConnection.connect(SQLServerConnection.java:1836) ~[mssql-jdbc-12.4.2.jre11.jar!/:na]
	at com.microsoft.sqlserver.jdbc.SQLServerDriver.connect(SQLServerDriver.java:1246) ~[mssql-jdbc-12.4.2.jre11.jar!/:na]
	at com.zaxxer.hikari.util.DriverDataSource.getConnection(DriverDataSource.java:138) ~[HikariCP-5.0.1.jar!/:na]
	at com.zaxxer.hikari.pool.PoolBase.newConnection(PoolBase.java:359) ~[HikariCP-5.0.1.jar!/:na]
	at com.zaxxer.hikari.pool.PoolBase.newPoolEntry(PoolBase.java:201) ~[HikariCP-5.0.1.jar!/:na]
	at com.zaxxer.hikari.pool.HikariPool.createPoolEntry(HikariPool.java:470) ~[HikariCP-5.0.1.jar!/:na]
	at com.zaxxer.hikari.pool.HikariPool.checkFailFast(HikariPool.java:561) ~[HikariCP-5.0.1.jar!/:na]
	at com.zaxxer.hikari.pool.HikariPool.<init>(HikariPool.java:100) ~[HikariCP-5.0.1.jar!/:na]
	at com.zaxxer.hikari.HikariDataSource.getConnection(HikariDataSource.java:112) ~[HikariCP-5.0.1.jar!/:na]
	at org.springframework.jdbc.datasource.DataSourceUtils.fetchConnection(DataSourceUtils.java:160) ~[spring-jdbc-6.1.5.jar!/:6.1.5]
	at org.springframework.jdbc.datasource.DataSourceUtils.doGetConnection(DataSourceUtils.java:118) ~[spring-jdbc-6.1.5.jar!/:6.1.5]
	at org.springframework.jdbc.datasource.DataSourceUtils.getConnection(DataSourceUtils.java:81) ~[spring-jdbc-6.1.5.jar!/:6.1.5]
	at org.springframework.jdbc.core.JdbcTemplate.execute(JdbcTemplate.java:342) ~[spring-jdbc-6.1.5.jar!/:6.1.5]
	at org.springframework.boot.jdbc.EmbeddedDatabaseConnection.isEmbedded(EmbeddedDatabaseConnection.java:168) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.autoconfigure.orm.jpa.HibernateDefaultDdlAutoProvider.getDefaultDdlAuto(HibernateDefaultDdlAutoProvider.java:42) ~[spring-boot-autoconfigure-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.autoconfigure.orm.jpa.HibernateJpaConfiguration.lambda$getVendorProperties$1(HibernateJpaConfiguration.java:142) ~[spring-boot-autoconfigure-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.autoconfigure.orm.jpa.HibernateSettings.getDdlAuto(HibernateSettings.java:41) ~[spring-boot-autoconfigure-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.autoconfigure.orm.jpa.HibernateProperties.determineDdlAuto(HibernateProperties.java:118) ~[spring-boot-autoconfigure-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.autoconfigure.orm.jpa.HibernateProperties.getAdditionalProperties(HibernateProperties.java:87) ~[spring-boot-autoconfigure-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.autoconfigure.orm.jpa.HibernateProperties.determineHibernateProperties(HibernateProperties.java:80) ~[spring-boot-autoconfigure-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.autoconfigure.orm.jpa.HibernateJpaConfiguration.getVendorProperties(HibernateJpaConfiguration.java:143) ~[spring-boot-autoconfigure-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.autoconfigure.orm.jpa.JpaBaseConfiguration.entityManagerFactory(JpaBaseConfiguration.java:132) ~[spring-boot-autoconfigure-3.2.4.jar!/:3.2.4]
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[na:na]
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(Unknown Source) ~[na:na]
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source) ~[na:na]
	at java.base/java.lang.reflect.Method.invoke(Unknown Source) ~[na:na]
	at org.springframework.beans.factory.support.SimpleInstantiationStrategy.instantiate(SimpleInstantiationStrategy.java:140) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.ConstructorResolver.instantiate(ConstructorResolver.java:644) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.ConstructorResolver.instantiateUsingFactoryMethod(ConstructorResolver.java:636) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.instantiateUsingFactoryMethod(AbstractAutowireCapableBeanFactory.java:1335) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1165) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:562) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:326) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:324) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.context.support.AbstractApplicationContext.getBean(AbstractApplicationContext.java:1234) ~[spring-context-6.1.5.jar!/:6.1.5]
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952) ~[spring-context-6.1.5.jar!/:6.1.5]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624) ~[spring-context-6.1.5.jar!/:6.1.5]
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:334) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1354) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1343) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at com.r2d2.qiss.R2D2QissApplication.main(R2D2QissApplication.java:14) ~[!/:1.0.0]
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[na:na]
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(Unknown Source) ~[na:na]
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source) ~[na:na]
	at java.base/java.lang.reflect.Method.invoke(Unknown Source) ~[na:na]
	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91) ~[r2d2-qiss-1.0.0.jar:1.0.0]
	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53) ~[r2d2-qiss-1.0.0.jar:1.0.0]
	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58) ~[r2d2-qiss-1.0.0.jar:1.0.0]
Caused by: java.net.SocketException: Connection reset
	at java.base/sun.nio.ch.NioSocketImpl.implRead(Unknown Source) ~[na:na]
	at java.base/sun.nio.ch.NioSocketImpl.read(Unknown Source) ~[na:na]
	at java.base/sun.nio.ch.NioSocketImpl$1.read(Unknown Source) ~[na:na]
	at java.base/java.net.Socket$SocketInputStream.read(Unknown Source) ~[na:na]
	at com.microsoft.sqlserver.jdbc.TDSChannel$ProxyInputStream.readInternal(IOBuffer.java:1197) ~[mssql-jdbc-12.4.2.jre11.jar!/:na]
	at com.microsoft.sqlserver.jdbc.TDSChannel$ProxyInputStream.read(IOBuffer.java:1183) ~[mssql-jdbc-12.4.2.jre11.jar!/:na]
	at com.microsoft.sqlserver.jdbc.TDSChannel.read(IOBuffer.java:2155) ~[mssql-jdbc-12.4.2.jre11.jar!/:na]
	... 58 common frames omitted

2025-04-16T10:14:12.251-04:00  INFO 16 --- [           main] o.hibernate.jpa.internal.util.LogHelper  : HHH000204: Processing PersistenceUnitInfo [name: default]
2025-04-16T10:14:12.377-04:00  INFO 16 --- [           main] org.hibernate.Version                    : HHH000412: Hibernate ORM core version 6.4.4.Final
2025-04-16T10:14:12.471-04:00  INFO 16 --- [           main] o.h.c.internal.RegionFactoryInitiator    : HHH000026: Second-level cache disabled
2025-04-16T10:14:12.746-04:00  WARN 16 --- [           main] ConfigServletWebServerApplicationContext : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: jakarta/xml/bind/JAXBException
2025-04-16T10:14:12.749-04:00  INFO 16 --- [           main] o.apache.catalina.core.StandardService   : Stopping service [Tomcat]
2025-04-16T10:14:12.762-04:00  INFO 16 --- [           main] .s.b.a.l.ConditionEvaluationReportLogger : 

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2025-04-16T10:14:12.784-04:00 ERROR 16 --- [           main] o.s.boot.SpringApplication               : Application run failed

org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: jakarta/xml/bind/JAXBException
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1786) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:326) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:324) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.context.support.AbstractApplicationContext.getBean(AbstractApplicationContext.java:1234) ~[spring-context-6.1.5.jar!/:6.1.5]
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952) ~[spring-context-6.1.5.jar!/:6.1.5]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624) ~[spring-context-6.1.5.jar!/:6.1.5]
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:334) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1354) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1343) ~[spring-boot-3.2.4.jar!/:3.2.4]
	at com.r2d2.qiss.R2D2QissApplication.main(R2D2QissApplication.java:14) ~[!/:1.0.0]
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[na:na]
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(Unknown Source) ~[na:na]
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source) ~[na:na]
	at java.base/java.lang.reflect.Method.invoke(Unknown Source) ~[na:na]
	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91) ~[r2d2-qiss-1.0.0.jar:1.0.0]
	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53) ~[r2d2-qiss-1.0.0.jar:1.0.0]
	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58) ~[r2d2-qiss-1.0.0.jar:1.0.0]
Caused by: java.lang.NoClassDefFoundError: jakarta/xml/bind/JAXBException
	at org.hibernate.boot.spi.XmlMappingBinderAccess.<init>(XmlMappingBinderAccess.java:45) ~[hibernate-core-6.4.4.Final.jar!/:6.4.4.Final]
	at org.hibernate.boot.MetadataSources.getXmlMappingBinderAccess(MetadataSources.java:119) ~[hibernate-core-6.4.4.Final.jar!/:6.4.4.Final]
	at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.prepare(MetadataBuildingProcess.java:153) ~[hibernate-core-6.4.4.Final.jar!/:6.4.4.Final]
	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.<init>(EntityManagerFactoryBuilderImpl.java:296) ~[hibernate-core-6.4.4.Final.jar!/:6.4.4.Final]
	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.<init>(EntityManagerFactoryBuilderImpl.java:198) ~[hibernate-core-6.4.4.Final.jar!/:6.4.4.Final]
	at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:63) ~[spring-orm-6.1.5.jar!/:6.1.5]
	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390) ~[spring-orm-6.1.5.jar!/:6.1.5]
	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409) ~[spring-orm-6.1.5.jar!/:6.1.5]
	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396) ~[spring-orm-6.1.5.jar!/:6.1.5]
	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366) ~[spring-orm-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1833) ~[spring-beans-6.1.5.jar!/:6.1.5]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1782) ~[spring-beans-6.1.5.jar!/:6.1.5]
	... 23 common frames omitted
Caused by: java.lang.ClassNotFoundException: jakarta.xml.bind.JAXBException
	at java.base/java.net.URLClassLoader.findClass(Unknown Source) ~[na:na]
	at java.base/java.lang.ClassLoader.loadClass(Unknown Source) ~[na:na]
	at org.springframework.boot.loader.net.protocol.jar.JarUrlClassLoader.loadClass(JarUrlClassLoader.java:104) ~[r2d2-qiss-1.0.0.jar:1.0.0]
	at org.springframework.boot.loader.launch.LaunchedClassLoader.loadClass(LaunchedClassLoader.java:91) ~[r2d2-qiss-1.0.0.jar:1.0.0]
	at java.base/java.lang.ClassLoader.loadClass(Unknown Source) ~[na:na]
	... 35 common frames omitted

