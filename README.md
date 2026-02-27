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
Hosted on Nvidia A10 GPU 24GB with CUDA 13.1
```shell
conda create -n vllm python=3.13
pip install vllm --extra-index-url https://download.pytorch.org/whl/cu131 --force-reinstall
pip install --upgrade transformers
vllm serve zai-org/GLM-OCR   --allowed-local-media-path /   --port 8080   --served-model-name glm-ocr   --speculative-config '{"method": "mtp", "num_speculative_tokens": 1}'   --limit-mm-per-prompt '{"image": 10}'   --max-model-len 30000
```
## Examples
![2024182848](https://github.com/user-attachments/assets/7d16885e-567a-4fe4-8049-8fdb07e43390)
```html
<table><thead><tr><th>QUANTITY</th><th>U of M</th><th>DESCRIPTION</th><th>NOT TO EXCEED</th><th>UNIT PRICE</th><th>TOTAL PRICE</th></tr></thead><tbody><tr><td>2</td><td>EA</td><td>ZR623020; 2½ x 50 x 50 Sheet Zucconia Ceramic Sheet</td><td></td><td></td><td>47600</td></tr><tr><td></td><td></td><td>Ship to: Alabama Research 152 Metal Strips Road P.O. Box 739 Murford, AL 36268</td><td></td><td></td><td></td></tr><tr><td></td><td></td><td>Att: Mr. Tom Kochan</td><td></td><td></td><td>2023636688</td></tr></tbody></table>
```
![2023636688](https://github.com/user-attachments/assets/666e4d1c-011f-42d4-a433-a13982bef752)

