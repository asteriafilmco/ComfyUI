# To start

```
conda activate comfyenv
python main.py
```

# Dev mode with paid nodes
Start comfy with 
```
python main.py --comfy-api-base https://stagingapi.comfy.org
```
Sign in with your Comfy API key:
```
comfy-API-key: comfyui-3a34d6aa99bb4dfb0e2badb936f369fcd1cd35061998e6ea0f1a59aee5f04ab4
```

# Download latest API from staging
```
curl -o openapi.yaml https://stagingapi.comfy.org/openapi
```
```
redocly bundle openapi.yaml --output filtered-openapi.yaml --config comfy_api_nodes/redocly-dev.yaml --remove-unused-components
```
```
datamodel-codegen --use-subclass-enum --field-constraints --strict-types bytes --input filtered-openapi.yaml --output comfy_api_nodes/apis/__init__.py --output-model-type pydantic_v2.BaseModel
```
source: https://github.com/Comfy-Org/ComfyUI-private/blob/master/comfy_api_nodes/README.md 