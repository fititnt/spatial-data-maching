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

## Quickstart to internals

After data is imported into memory, it's organized similar to a GeoJSON feature. Two extra references:

- `@fid`: file identifier (unique). A sequential number, starting from 1, by default based on the order of import
- `@tid`: items identifier (unique). A sequential number, starting from 1, based on order of files **and** order of itens in the files.


<!--

@TODO implement these shortcuts to create implicit queries to match objects


## MS "Match Strategy"
### For strict strategy, terms after 2nd // are keys, split by |
//MS//website

//MS//addr:street
//MS//addr:housenumber

//MS//addr:street|addr:housenumber|amenity
//MS//wikidata

-->

## Quickstart to debug

1. Using the console of your browser, the variable `SDMData` will contain most of the underlining data of the memory (the v0.5.0 the close equivalent would be `WorkingData`). The `SDMConf` also contains some internal configurations and reference to some options defined by the user.
