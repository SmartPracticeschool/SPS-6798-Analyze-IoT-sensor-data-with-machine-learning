# SPS-6798-Analyze-IoT-sensor-data-with-machine-learning
Analyze IoT sensor data with machine learning
Python code snippetts for ML model deployed

import requests

# NOTE: you must manually set API_KEY below using information retrieved from your IBM Cloud account.
API_KEY = "<your API key>"
token_response = requests.post('https://iam.eu-gb.bluemix.net/identity/token', data={"apikey": API_KEY, "grant_type": 'urn:ibm:params:oauth:grant-type:apikey'})
mltoken = token_response.json()["access_token"]

header = {'Content-Type': 'application/json', 'Authorization': 'Bearer ' + mltoken}

# NOTE: manually define and pass the array(s) of values to be scored in the next line
payload_scoring = {"fields": [array_of_input_fields], "values": [array_of_values_to_be_scored, another_array_of_values_to_be_scored]}

response_scoring = requests.post('https://eu-gb.ml.cloud.ibm.com/ml/v4/deployments/1038769f-9222-4355-b9a1-19b5c6d73bd9/predictions?version=2020-10-28', json=payload_scoring, headers={'Authorization': 'Bearer ' + mltoken})
print("Scoring response")
print(response_scoring.json())


nodeRed url:
https://node-red-dbxco-2020-10-24.eu-gb.mybluemix.net/red/#flow/d709258c.a84888

Dataset name iotdata created from ML model deployed which is to be given as input in node Red flow:
https://node-red-dbxco-2020-10-24.eu-gb.mybluemix.net/ui/#!/0?socketid=_TIOT6ftyk-kdQDpAAAg

IoT platform sensor internal simulator activated results visualized from boards and cards created while running it:
https://n3hxqh.internetofthings.ibmcloud.com/dashboard/boards/3dde7934-e244-4e88-8470-3b38b008d26c

Event payload for the simulator activated:
https://n3hxqh.internetofthings.ibmcloud.com/dashboard/devices/browse
