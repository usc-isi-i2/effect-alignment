# Elastic Search Mappings for Effect

To create the Elastic Search Mappings automatically,

1. Change the config-es-mappings.json. If there are new frames, they need to be defined at the end of the file

2. Run the script `create-mapping.py` available in dig-alignment repo: https://github.com/usc-isi-i2/dig-alignment/tree/development/scripts/python with input as this config-es-mappings.json file and the output as es-mappings.json
```
python create-mapping.py ~/github/effect/effect-alignment/es/config-es-mappings.json ~/github/effect/effect-alignment/es/es-mappings.json
```

The final `es-mappings.json` should be used to create the effect index.
