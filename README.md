import org.apache.http.impl.client.CloseableHttpClient;
import org.apache.http.impl.client.HttpClients;
import org.apache.http.impl.client.LaxRedirectStrategy;
import org.springframework.http.client.HttpComponentsClientHttpRequestFactory;

public class DatabricksOAuthService {

    public String getAccessToken() {
        String tokenUrl = "https://login.microsoftonline.com/5d3e2773-e07f-4432-a630-1a0f68a28a05/oauth2/v2.0/token";

        CloseableHttpClient httpClient = HttpClients.custom()
                .setRedirectStrategy(new LaxRedirectStrategy()) // Enables following 302 redirects
                .build();

        RestTemplate restTemplate = new RestTemplate(new HttpComponentsClientHttpRequestFactory(httpClient));

        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.APPLICATION_FORM_URLENCODED);

        MultiValueMap<String, String> body = new LinkedMultiValueMap<>();
        body.add("client_id", clientId);
        body.add("client_secret", clientSecret);
        body.add("scope", "https://databricks.azure.com/.default");
        body.add("grant_type", "client_credentials");

        HttpEntity<MultiValueMap<String, String>> request = new HttpEntity<>(body, headers);

        ResponseEntity<Map> response = restTemplate.postForEntity(tokenUrl, request, Map.class);

        if (response.getStatusCode().is2xxSuccessful() && response.getBody() != null) {
            return response.getBody().get("access_token").toString();
        } else {
            throw new RuntimeException("OAuth Token Request Failed: " + response.getBody());
        }
    }
}
