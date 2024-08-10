# tests/


<!--

- http://git.workspace.localhost/fititnt/spatial-data-maching/public/?data[]=https://sdmtestdata.etica.ai/d/hospital.076.osm.geojson&data[]=https://sdmtestdata.etica.ai/d/hospital.001.wikidata.tsv



- http://git.workspace.localhost/fititnt/spatial-data-maching/public/?conf[]=https://raw.githubusercontent.com/fititnt/spatial-data-maching/main/tests/test-1.sdm.yml&data[]=https://sdmtestdata.etica.ai/d/hospital.076.osm.geojson&data[]=https://sdmtestdata.etica.ai/d/hospital.001.wikidata.tsv


http://git.workspace.localhost/fititnt/spatial-data-maching/public/?conf[]=https://raw.githubusercontent.com/fititnt/spatial-data-maching/main/tests/test-1.sdm.yml&data[]=https://sdmtestdata.etica.ai/d/countries.001.osm.geojson&data[]=https://sdmtestdata.etica.ai/d/countries.001.wikidata.tsv&data[]=https://sdmtestdata.etica.ai/d/countries-territories-unocha.001.hxl.csv


@TODO 1. make conf files without data and at same time load the data by URL parameters
@TODO 2. make conf files with one dataset and at same time load other datasets data by URL parameters, as if the first dataset could be considered a default value for target conflation (if not specified other value)

-->

- https://sdm.etica.ai/v/0.6.0b2/?conf[]=https://sdmtestdata.etica.ai/c/file-not-exists.sdm.yml
  - Expected: Should report critical error (configuration file not exist)
- https://sdm.etica.ai/v/0.6.0b2/?conf[]=https://sdmtestdata.etica.ai/c/test-000.sdm.yml
  - Expected: Should report no dataset found
- https://sdm.etica.ai/v/0.6.0b2/?conf[]=https://sdmtestdata.etica.ai/c/test-001.sdm.yml
- https://sdm.etica.ai/v/0.6.0b2/?conf[]=https://sdmtestdata.etica.ai/c/test-002.sdm.yml
- https://sdm.etica.ai/v/0.6.0b2/?conf[]=https://sdmtestdata.etica.ai/c/test-004.sdm.yml
  - Should work (file needs update hospital.001.osm.geojsonl -> countries.001.osm.geojsonl)
- https://sdm.etica.ai/v/0.6.0b2/?conf[]=https://sdmtestdata.etica.ai/c/test-005.sdm.yml&conf[]=https://sdmtestdata.etica.ai/c/test-006.sdm.yml
  - The data files are divided in 2 configuration files
  - Currently it is considering only the lastest data
  - Maybe merge the datafiles? Or make it configurable?
- https://sdm.etica.ai/v/0.6.0b2/?data[]=https://sdmtestdata.etica.ai/d/countries.001.osm.geojson&data[]=https://sdmtestdata.etica.ai/d/countries.001.wikidata.tsv&data[]=https://sdmtestdata.etica.ai/d/countries-territories-unocha.001.hxl.csv