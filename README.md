package com.r2d2.qiss.util;

import org.springframework.beans.factory.annotation.Value;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.jdbc.datasource.SimpleDriverDataSource;
import com.databricks.client.jdbc.Driver;
import org.springframework.stereotype.Component;

@Component
public class DatabricksJdbcTemplateFactory {

    @Value("${databricks.base.url}")
    private String baseUrl;

    @Value("${databricks.http.path}")
    private String httpPath;

    @Value("${databricks.common.params}")
    private String commonParams;

    public JdbcTemplate createJdbcTemplate(String token) {
        String jdbcUrlWithToken = String.format(
            "%shttpPath=%s;%s;Auth_AccessToken=%s",
            baseUrl, httpPath, commonParams, token
        );

        SimpleDriverDataSource dataSource = new SimpleDriverDataSource();
        dataSource.setDriverClass(Driver.class);
        dataSource.setUrl(jdbcUrlWithToken);

        return new JdbcTemplate(dataSource);
    }
}












Step 2: Config Class

Create DatabricksConfig.java to configure the DataSource and JdbcTemplate:

import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.jdbc.datasource.SimpleDriverDataSource;

import javax.sql.DataSource;
import com.databricks.client.jdbc.Driver;

@Configuration
public class DatabricksConfig {

    @Value("${spring.datasource.url}")
    private String jdbcUrl;

    @Bean
    public DataSource databricksDataSource() {
        SimpleDriverDataSource dataSource = new SimpleDriverDataSource();
        dataSource.setDriverClass(Driver.class);
        dataSource.setUrl(jdbcUrl);
        return dataSource;
    }

    @Bean
    public JdbcTemplate jdbcTemplate(DataSource databricksDataSource) {
        return new JdbcTemplate(databricksDataSource);
    }
}

Step 3: Create Service to Run Query

Create DatabricksService.java:

import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.stereotype.Service;

import java.util.List;
import java.util.Map;

@Service
public class DatabricksService {

    private final JdbcTemplate jdbcTemplate;

    public DatabricksService(JdbcTemplate jdbcTemplate) {
        this.jdbcTemplate = jdbcTemplate;
    }

    public List<Map<String, Object>> getHolidayCalendar() {
        String query = "select * from hive_metastore.inv_semantic_qdb.holiday_calendar limit 100";
        return jdbcTemplate.queryForList(query);
    }
}

Step 4: Create Controller to Expose API

Create DatabricksController.java:

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;
import java.util.Map;

@RestController
@RequestMapping("/api/databricks")
public class DatabricksController {

    private final DatabricksService databricksService;

    public DatabricksController(DatabricksService databricksService) {
        this.databricksService = databricksService;
    }

    @GetMapping("/holidays")
    public List<Map<String, Object>> fetchHolidayCalendar() {
        return databricksService.getHolidayCalendar();
    }
}

Project Structure Example

src/main/java/
├── com.yourpackage
│   ├── DatabricksConfig.java
│   ├── DatabricksService.java
│   ├── DatabricksController.java
│   ├── Application.java

Step 5: Example application.properties (Complete)

server.port=8080

databricks.host=adb-1234567890123456.7.azuredatabricks.net
databricks.httpPath=/sql/1.0/warehouses/1234567890abcdef
databricks.token=your-personal-access-token

spring.datasource.driver-class-name=com.databricks.client.jdbc.Driver
spring.datasource.url=jdbc:databricks://${databricks.host}:443/default;transportMode=http;ssl=1;httpPath=${databricks.httpPath};AuthMech=11;Auth_Flow=0;UseNativeQuery=0;Auth_AccessToken=${databricks.token}

Step 6: Run and Test

Start your Spring Boot app, and test:

GET http://localhost:8080/api/databricks/holidays

This will return the 100 records from your table as JSON.

Bonus Tip: Secure Secrets

For production, never hard-code tokens in properties files. Use Azure Key Vault, environment variables, or a secrets manager instead.

Summary

Component	File
Config	DatabricksConfig.java
Service	DatabricksService.java
Controller	DatabricksController.java
Config File	application.properties

Want me to generate a ready-to-run zip file for this? Let me know! I can bundle it for you and you can just copy it into your project.
