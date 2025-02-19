databricks.oauth.client-id=b2d94b7e-b35b-4567-8395-9ac2edad50de
databricks.oauth.client-secret=fn78Qo~lUJ9FNYFPBgLcvfto_oX336-lWelCPcdd
databricks.oauth.tenant-id=5d3e2773-e07f-4432-a630-1a0f68a28a05
databricks.oauth.token-url=https://login.microsoftonline.com/${databricks.oauth.tenant-id}/oauth2/v2.0/token

import org.springframework.http.*;
import org.springframework.stereotype.Service;
import org.springframework.web.client.RestTemplate;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.util.LinkedMultiValueMap;
import org.springframework.util.MultiValueMap;
import com.fasterxml.jackson.databind.JsonNode;
import com.fasterxml.jackson.databind.ObjectMapper;
import java.util.Objects;

@Service
public class DatabricksOAuthService {

    @Value("${databricks.oauth.client-id}")
    private String clientId;

    @Value("${databricks.oauth.client-secret}")
    private String clientSecret;

    @Value("${databricks.oauth.token-url}")
    private String tokenUrl;

    private final RestTemplate restTemplate = new RestTemplate();

    public String getAccessToken() {
        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.APPLICATION_FORM_URLENCODED);

        MultiValueMap<String, String> body = new LinkedMultiValueMap<>();
        body.add("client_id", clientId);
        body.add("client_secret", clientSecret);
        body.add("scope", "https://databricks.azure.com/.default");
        body.add("grant_type", "client_credentials");

        HttpEntity<MultiValueMap<String, String>> request = new HttpEntity<>(body, headers);

        ResponseEntity<String> response = restTemplate.exchange(tokenUrl, HttpMethod.POST, request, String.class);

        if (response.getStatusCode().is2xxSuccessful()) {
            try {
                ObjectMapper objectMapper = new ObjectMapper();
                JsonNode jsonNode = objectMapper.readTree(Objects.requireNonNull(response.getBody()));
                return jsonNode.get("access_token").asText();
            } catch (Exception e) {
                throw new RuntimeException("Error parsing OAuth token response", e);
            }
        } else {
            throw new RuntimeException("OAuth Token Request Failed: " + response.getBody());
        }
    }
}