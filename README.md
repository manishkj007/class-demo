# class-demo
curl -X POST https://login.microsoftonline.com/5d3e2773-e07f-4432-a630-1a0f68a28a05/oauth2/v2.0/token \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -d "client_id=b2d94b7e-b35b-4567-8395-9ac2edad50de" \
     -d "client_secret=fn78Qo~lUJ9FNYFPBgLcvfto_oX336-lWelCPcdd" \
     -d "scope=https://databricks.azure.com/.default" \
     -d "grant_type=client_credentials"
