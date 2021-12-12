# gCloud Service Account credentials for local development

If running this  [Google Translate" app locally on Flask Codelab](https://codelabs.developers.google.com/codelabs/cloud-nebulous-serverless-python-flask?hl=en#0) there is a requirement to set GOOGLE_APPLICATION_CREDENTIALS explicitly, this can be done by exporting as an env variable. A possible error if this is not exported is;

`google.auth.exceptions.DefaultCredentialsError: Could not automatically determine credentials. Please set GOOGLE_APPLICATION_CREDENTIALS or explicitly create credentials and re-run the application. For more information, please see https://cloud.google.com/docs/authentication/getting-started`

# Python workaround to permanently add the json file into the code

Add these lines of code to the main.py [sample code](https://github.com/googlecodelabs/cloud-nebulous-serverless)  
1. Import service account module  
`from google.oauth2 import service_account`

2. create a variable that stores the credentials  
`GOOGLE_APPLICATION_CREDENTIALS = service_account.Credentials.from_service_account_file("path to file.json")`

3. use the credentials in the translate service client  
`TRANSLATE = translate.TranslationServiceClient(credentials = GOOGLE_APPLICATION_CREDENTIALS)`


