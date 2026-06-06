# IBM-AI-Internship-project
The cURL code for the AIML project on the topic - Power System Fault Detection and Classification :
# NOTE: you must set $API_KEY below using information retrieved from your IBM Cloud account (https://au-syd.dai.cloud.ibm.com/docs/content/wsj/analyze-data/ml-authentication.html?context=wx)

export API_KEY=<your API key>

export IAM_TOKEN=$(curl --insecure -X POST --location "https://iam.cloud.ibm.com/identity/token" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" --data-urlencode "apikey=$API_KEY" | jq -r '.access_token')

# TODO:  manually define and pass values to be scored below

curl --location "https://private.au-syd.ml.cloud.ibm.com/ml/v4/deployments/019e9c82-a53a-7551-a806-e963c84aa6ee/predictions?version=2021-05-01" --header "Content-Type: application/json" --header "Accept: application/json" --header "Authorization: Bearer $IAM_TOKEN" --data '{
		 "input_data": [
		     {
		         "fields": [$ARRAY_OF_INPUT_FIELDS],
		         "values": [[$ARRAY_OF_VALUES_TO_BE_SCORED], [$ANOTHER_ARRAY_OF_VALUES_TO_BE_SCORED]]
		     }
		 ]
}'



The Endpoint link of the deployed project is-https://au-syd.ml.cloud.ibm.com/ml/v4/deployments/019e9c82-a53a-7551-a806-e963c84aa6ee/predictions?version=2021-05-01
