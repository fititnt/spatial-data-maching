# spatial-data-maching

See <https://www.openstreetmap.org/user/fititnt/diary/404303>.

TL;DR:
1. Allows visualize datasets, with special focus with spatial reference (e.g. position on earth), and export the results of your filters to other programs
2. Can be used to load data and then as a companion (side by side or _alt tabbing_) with other editing tools (OpenStreetMap, Wikidata, reviewing data from the government/company you work, etc).
3. The internal data model uses GeoJSON. It also allows importing tabular data, trying to auto detect latitude and longitude
4. **There's no "automatic conflation button"**. You need to explore how datasets are related to each other, such as deciding distance and/or attributes in common, **then** it can assist you.

## Configuration
_to be documented_

The [JSON-Schema](https://json-schema.org/) for the latest version is available at [public/sdm.schema.json](public/sdm.schema.json).
This schema can be used to strictly document and validate configuration files, such as examples on the filter tests/.


## Quickstart to debug

1. Using the console of your browser, the variable `SDMData` will contain most of the underlining data of the memory (the v0.5.0 the close equivalent would be `WorkingData`). The `SDMConf` also contains some internal configurations and reference to some options defined by the user.
