# SPS-6798-Analyze-IoT-sensor-data-with-machine-learning
Analyze IoT sensor data with machine learning
code snippetts for ML model deployed
Code Snippetts:
import requests
# NOTE: you must manually set API_KEY below using information retrieved from your IBM Cloud account.
API_KEY = "<your API key>"
token_response = requests.post('https://iam.ng.bluemix.net/identity/token', data={"apikey": API_KEY, "grant_type": 'urn:ibm:params:oauth:grant-type:apikey'})
mltoken = token_response.json()["access_token"]

header = {'Content-Type': 'application/json', 'Authorization': 'Bearer ' + mltoken}

# NOTE: manually define and pass the array(s) of values to be scored in the next line
payload_scoring = {"fields": [array_of_input_fields], "values": [array_of_values_to_be_scored, another_array_of_values_to_be_scored]}

response_scoring = requests.post('https://us-south.ml.cloud.ibm.com/ml/v4/deployments/a41efc63-1138-4ad2-981e-5976121f2395/predictions?version=2020-10-23', json=payload_scoring, headers={'Authorization': 'Bearer ' + mltoken})
print("Scoring response")
print(response_scoring.json())


Python code of the tested output of the deployed model:
{
    "predictions": [
        {
            "fields": [
                "prediction",
                "probability"
            ],
            "values": [
                [
                    0,
                    [
                        0.8140779733657837,
                        0.18592201173305511
                    ]
                ]
            ]
        }
    ]
}

nodeRed url:
https://node-red-dbxco-2020-10-24.eu-gb.mybluemix.net/red/#flow/d709258c.a84888

Dataset name iotdata created from ML model deployed which is to be given as input in node Red flow:
https://node-red-dbxco-2020-10-24.eu-gb.mybluemix.net/ui/#!/0?socketid=SqNNe4wqxE-FQlBVAAAh

IoT platform sensor internal simulator activated results visualized from boards and cards created while running it:
https://wy3fg4.internetofthings.ibmcloud.com/dashboard/boards/62696e84-b970-43bd-97c5-d452ce9073dd

Event payload for the simulator activated:
https://wy3fg4.internetofthings.ibmcloud.com/dashboard/devices/browse
