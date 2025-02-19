import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.boot.jdbc.DataSourceBuilder;
import javax.sql.DataSource;

@Configuration
public class DatabricksConfig {

    @Autowired
    private DatabricksOAuthService databricksOAuthService;

    @Value("${spring.datasource.driver-class-name}")
    private String driverClassName;

    @Value("${spring.datasource.host}")
    private String databricksHost;

    @Value("${databricks.warehouse.id}")
    private String warehouseId;

    @Value("${databricks.http-path}") // Make sure to define this in application.properties
    private String httpPath;

    @Bean(name = "databricksDataSource")
    public DataSource dataSource() {
        String accessToken = databricksOAuthService.getAccessToken();

        if (accessToken == null || accessToken.isEmpty()) {
            throw new RuntimeException("🔴 ERROR: OAuth Token retrieval failed.");
        }

        // Construct Correct JDBC URL with httpPath
        String jdbcUrl = "jdbc:databricks://" + databricksHost + ":443" +
                "/sql/protocolv1/o/7326973620544214/" + warehouseId +
                ";httpPath=" + httpPath +
                ";AuthMech=3;UID=token;PWD=" + accessToken;

        // Debugging: Print Connection URL (Masked Token)
        System.out.println("🔹 JDBC Connection URL: " + jdbcUrl.replace(accessToken, "********"));

        return DataSourceBuilder.create()
                .url(jdbcUrl)
                .driverClassName(driverClassName)
                .build();
    }
}


spring.datasource.driver-class-name=com.databricks.client.jdbc.Driver
spring.datasource.host=adb-7326973620544214.azuredatabricks.net
databricks.warehouse.id=161273606e371f1  # From Postman response
databricks.http-path=/sql/1.0/endpoints/161273606e371f1  # Get this from Databricks UI

