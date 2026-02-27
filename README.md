# OCR Project

## Overview
Perform Layout Identification and extract information from images.

## Setup .env file
```shell
MODEL_PATH=zai-org/GLM-OCR
GLMOCR_OCR_API_HOST=
GLMOCR_OCR_API_PORT=8080
GLMOCR_MODE=selfhosted
```
## Setup Client
```shell
conda create -n client python=3.13
conda active client
pip install -r requirements.txt
```
## Setup Server for OCR API
Hosted on Nvidia A10 GPU 24GB
```shell
conda create -n vllm python=3.13
pip install vllm --extra-index-url https://download.pytorch.org/whl/cu131 --force-reinstall
pip install --upgrade transformers
vllm serve zai-org/GLM-OCR   --allowed-local-media-path /   --port 8080   --served-model-name glm-ocr   --speculative-config '{"method": "mtp", "num_speculative_tokens": 1}'   --limit-mm-per-prompt '{"image": 10}'   --max-model-len 30000
```
## Examples
