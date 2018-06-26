# effect-alignment

This repository will contain the Karma models, frames, etc that can be made public.
No sample data should be added to this repo. It should be added to the effect-data repository.

The [dig-alignment](https://github.com/usc-isi-i2/dig-alignment) repository will hold the ontologies, context and the python scripts.
You need to clone and checkout the **development** branch and set Karma home as `<clone folder>/dig-alignment/versions/3.0/karma/`. For  example: `/Users/usc/github/dig/dig-alignment/versions/3.0/karma/`

```
git clone https://github.com/usc-isi-i2/dig-alignment.git
git checkout development
```



## Incorporating a New Source
1. Download a sample data for the source
2. Convert the data into Json Lines: `jq -c .[] filename.json > filename.jl`
3. Convert the data into CDR - `python generateDataForKarmaModeling.py --input filename.jl \
          --output filename-CDR.jl --source <sourcename>` 
   Follow steps [here](https://github.com/usc-isi-i2/effect-workflows) for installation(Steps 1-4)
4. Save the sample data files(json, jl, -cdr.jl) into effect-data repository)

5. Model the source in Karma

    a. You need to generate a minimum the ttl file, the md file and the -root.txt file. The folder should be named as the `<sourcename>`, consistent with above and what is mentioned in Step 5.
  
    b. If there is something that is not in the Ontology, you can add it to [dig-alignment](https://github.com/usc-isi-i2/dig-alignment/tree/development/versions/3.0/karma/preloaded-ontologies)
    
    c. For the properties added to existing Frames, add the property to frame in the "frames" folder. If new frame is needed to be generated, add the frame and update `ES/config-es-mappings.json`
    
    d. If the ontology or frames are changed, follow the README in the ES folder to update ES mappings. Note that the frames would need to be committed to github if they are changed as the code pulls it from github
     
6. Add the API for the new source and schedule / restart the coordinator for the API. The process would get just incremental data everyday, so you might need to run the workflow once to get the entire dataset for this source
