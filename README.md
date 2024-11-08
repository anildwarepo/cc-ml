
Install az cli


az login


az acr build --registry 00e650921d8a4308b9295c698bca5b08 --image cc-ml1 --file Dockerfile .

az ml environment create -f .\environment_acr\env.yml


az ml online-endpoint create -f .\endpoint\cc_endpoint.yml

az ml online-deployment create -f .\endpoint\cc_deployment_acr.yml

az ml online-deployment update -f .\endpoint\cc_deployment_acr.yml



