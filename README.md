<dependency>
    <groupId>com.squareup.okhttp3</groupId>
    <artifactId>okhttp</artifactId>
    <version>4.11.0</version>  <!-- Use the latest version -->
</dependency>

import okhttp3.*;
import org.springframework.stereotype.Service;
import java.io.IOException;
import java.util.Objects;

@Service
public class DatabricksOAuthService {

    private final String clientId = "b2d94b7e-b35b-4567-8395-9ac2edad50de";
    private final String clientSecret = "fn78Qo~lUJ9FNYFPBgLcvfto_oX336-lWelCPcdd";
    private final String tenantId = "5d3e2773-e07f-4432-a630-1a0f68a28a05";
    private final String tokenUrl = "https://login.microsoftonline.com/%s/oauth2/v2.0/token";

    private final OkHttpClient client = new OkHttpClient();

    public String getAccessToken() {
        String fullTokenUrl = String.format(tokenUrl, tenantId);

        // Create the request body with form-encoded data
        RequestBody body = new FormBody.Builder()
                .add("client_id", clientId)
                .add("client_secret", clientSecret)
                .add("scope", "https://databricks.azure.com/.default")
                .add("grant_type", "client_credentials")
                .build();

        // Create the HTTP request
        Request request = new Request.Builder()
                .url(fullTokenUrl)
                .post(body)
                .addHeader("Content-Type", "application/x-www-form-urlencoded")
                .build();

        try (Response response = client.newCall(request).execute()) {
            if (response.isSuccessful() && response.body() != null) {
                String responseBody = Objects.requireNonNull(response.body()).string();
                System.out.println("OAuth Response: " + responseBody);

                // Extract the access token from the response JSON
                return extractAccessToken(responseBody);
            } else {
                throw new RuntimeException("Failed to get OAuth token: " + response);
            }
        } catch (IOException e) {
            throw new RuntimeException("Error while requesting OAuth token", e);
        }
    }

    private String extractAccessToken(String jsonResponse) {
        // Basic way to extract access_token (use Jackson or Gson for better parsing)
        int start = jsonResponse.indexOf("access_token\":\"") + 15;
        int end = jsonResponse.indexOf("\"", start);
        return jsonResponse.substring(start, end);
    }
}