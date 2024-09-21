Azure Cloud Project for AI image Analysis and Generation

## create resource group
`az group create -g cloud-project-rg -l eastus`

Create azure cognitive service
az cognitiveservices account create --kind ComputerVision `
                                    --location eastus `
                                    --name cloud-ai-project-vision `
                                    --resource-group $env:rg `
                                    --sku F0 `
                                    --yes

create azure cognitive service of OpenAI kind
az cognitiveservices account create `
  --name my-openai-resource `
  --resource-group $env:rg `
  --kind OpenAI `
  --sku F0 `
  --location eastus `
  --yes

## To get the endpoints
az cognitiveservices account show --name  cloud-ai-project-vision --resource-group <$rg> | grep endpoint

## To get the Keys
az cognitiveservices account keys list --name cloud-ai-project-vision --resource-group $rg --query "key1"
az cognitiveservices account keys list --name my-openai-resource --resource-group $rg --query "key1"


## Azure Open AI SDK
`dotnet add package Azure.AI.OpenAI --prerelease`


## clean up
az group delete --name cloud-project-rg