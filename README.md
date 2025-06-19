# Intelligent PDF Summarizer with Azure Durable Functions

This project demonstrates how to build an intelligent PDF summarization pipeline using **Azure Durable Functions**, **Blob Storage**, **Azure Cognitive Services**, and **Azure OpenAI**. It showcases how to process PDF documents by extracting their content and summarizing them into concise insights using Azure AI tools.

![image](https://github.com/user-attachments/assets/f7b90a7d-f347-41e0-9203-6b5a350d400f)

## 🧩 Architecture Overview

```
graph TD
    A[PDF Uploaded to Blob Storage (Input Container)] --> B[Durable Function Trigger (Blob Upload)]
    B --> C[Activity 1: Extract Text using Azure Form Recognizer]
    C --> D[Activity 2: Summarize Text using Azure OpenAI]
    D --> E[Save Summary to Blob Storage (Output Container)]

```
---

## ⚙️ Features

- Triggered by PDF uploads in Blob Storage
- Text extraction using Azure Cognitive Services – Form Recognizer
- Summary generation using Azure OpenAI (GPT)
- Durable, fault-tolerant workflow using Azure Durable Functions
- Output written to separate output container
```

## 📋 Prerequisites

- Active Azure subscription
- Python 3.9+
- [Azure Functions Core Tools](https://learn.microsoft.com/en-us/azure/azure-functions/functions-run-local)
- [Azurite](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azurite) (local storage emulator)
- [Azure Developer CLI (azd)](https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli/install-azd)
- Permissions to create Azure resources (OpenAI, Cognitive Services, Blob Storage)
```
---

## 🛠 Local Setup Instructions

### 1. Clone the Repository

```bash
git clone <repo-url>
cd Intelligent-PDF-Summarizer
```
### 2. Create local.settings.json
Create a local.settings.json file in the project root:

```
{
  "IsEncrypted": false,
  "Values": {
    "AzureWebJobsStorage": "UseDevelopmentStorage=true",
    "AzureWebJobsFeatureFlags": "EnableWorkerIndexing",
    "FUNCTIONS_WORKER_RUNTIME": "python",
    "BLOB_STORAGE_ENDPOINT": "<your-blob-storage-endpoint>",
    "COGNITIVE_SERVICES_ENDPOINT": "<your-form-recognizer-endpoint>",
    "AZURE_OPENAI_ENDPOINT": "<your-openai-endpoint>",
    "AZURE_OPENAI_KEY": "<your-openai-key>",
    "CHAT_MODEL_DEPLOYMENT_NAME": "<your-model-deployment-name>"
  }
}
```

### 3. Install Python Dependencies
```
python3 -m pip install -r requirements.txt
```
### 4. Start Azurite (Local Storage Emulator)
```
azurite
```
Leave this terminal running.

### 5. Create Blob Containers
Using Azure Storage Explorer or the Azure Portal, create:
  - input container for uploading PDFs
  - output container for storing summaries

### 6. Start the Function App
```
func start --verbose
```

🚀 Using the App
  - Upload a .pdf file into the input container.
  - The Durable Function will extract and summarize the document.
  - Check the output container for the summarized result.

## Author
Satyam Panseriya

Video Demo Link : https://youtu.be/YTUuNd61ovc

