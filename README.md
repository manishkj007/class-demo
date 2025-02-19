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

    @Value("${databricks.warehouse.id}")
    private String warehouseId; // Use warehouse ID from Postman response

    @Value("${spring.datasource.driver-class-name}")
    private String driverClassName;

    @Value("${spring.datasource.host}")
    private String databricksHost; // Make sure to define this in application.properties

    @Bean(name = "databricksDataSource")
    public DataSource dataSource() {
        String accessToken = databricksOAuthService.getAccessToken();

        // Validate Token
        if (accessToken == null || accessToken.isEmpty()) {
            throw new RuntimeException("🔴 ERROR: OAuth Token retrieval failed.");
        }

        // Debugging: Print Access Token (Shortened for Security)
        System.out.println("🔹 OAuth Token: " + accessToken.substring(0, 30) + "...");

        // Correct JDBC URL using your working Warehouse ID
        String jdbcUrl = "jdbc:databricks://" + databricksHost + ":443/sql/protocolv1/o/7326973620544214/" + warehouseId +
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
databricks.warehouse.id=161273606e371f1  # Warehouse ID from Postman response




