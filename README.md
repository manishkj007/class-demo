import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.jdbc.datasource.DriverManagerDataSource;
import org.springframework.stereotype.Service;
import javax.sql.DataSource;
import java.util.List;
import java.util.Map;

@Service
public class DatabricksService {

    @Autowired
    private DatabricksOAuthService oAuthService;

    public List<Map<String, Object>> getDatabricksData(String tableName) {
        String accessToken = oAuthService.getAccessToken();

        DataSource dataSource = new DriverManagerDataSource(
                "jdbc:databricks://adb-7326973620544214.azuredatabricks.net:443/default;" +
                "transportMode=http;ssl=1;AuthMech=3;UID=token;PWD=" + accessToken
        );

        JdbcTemplate jdbcTemplate = new JdbcTemplate(dataSource);
        String query = "SELECT * FROM " + tableName + " LIMIT 10"; // Replace with actual table name
        return jdbcTemplate.queryForList(query);
    }
}




import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;
import java.util.List;
import java.util.Map;

@RestController
@RequestMapping("/api/databricks")
public class DatabricksController {

    @Autowired
    private DatabricksService databricksService;

    @GetMapping("/data")
    public List<Map<String, Object>> getDatabricksData(@RequestParam String table) {
        return databricksService.getDatabricksData(table);
    }
}

