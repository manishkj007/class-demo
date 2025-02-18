import org.springframework.http.HttpEntity;
import org.springframework.http.HttpHeaders;
import org.springframework.http.HttpMethod;
import org.springframework.http.MediaType;
import org.springframework.http.ResponseEntity;
import org.springframework.stereotype.Service;
import org.springframework.web.client.RestTemplate;
import org.springframework.util.LinkedMultiValueMap;
import org.springframework.util.MultiValueMap;

import java.util.Map;

@Service
public class DatabricksOAuthService {

    private final String clientId = "b2d94b7e-b35b-4567-8395-9ac2edad50de";
    private final String clientSecret = "fn78Qo~lUJ9FNYFPBgLcvfto_oX336-lWelCPcdd";
    private final String tenantId = "5d3e2773-e07f-4432-a630-1a0f68a28a05";
    private final String oauthUrl = "https://login.microsoftonline.com/%s/oauth2/v2.0/token";

    public String getAccessToken() {
        String tokenUrl = String.format(oauthUrl, tenantId);

        RestTemplate restTemplate = new RestTemplate();
        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.APPLICATION_FORM_URLENCODED);

        // Use MultiValueMap for correct encoding
        MultiValueMap<String, String> body = new LinkedMultiValueMap<>();
        body.add("client_id", clientId);
        body.add("client_secret", clientSecret);
        body.add("scope", "https://databricks.azure.com/.default");
        body.add("grant_type", "client_credentials");

        HttpEntity<MultiValueMap<String, String>> request = new HttpEntity<>(body, headers);

        ResponseEntity<Map> response = restTemplate.exchange(tokenUrl, HttpMethod.POST, request, Map.class);

        if (response.getStatusCode().is2xxSuccessful()) {
            System.out.println("OAuth Token Retrieved: " + response.getBody());
            return response.getBody().get("access_token").toString();
        } else {
            throw new RuntimeException("Failed to get Databricks OAuth token: " + response.getBody());
        }
    }
}
