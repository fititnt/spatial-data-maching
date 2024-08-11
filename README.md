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

- `@did`: dataset identifier (unique).
  - A sequential number, starting from 1, by default based on the order of import
- `@fid`: feature identifier (unique).
  - A sequential number, starting from 1, based on order of files **and** order of items in the files.
- `@mgi`: pattern matching identifier group.
  - For an given set of maching strategy, calculate for the entire target dataset. All features with same code are considered be the same group.
- `@mmi`: manual maching identifier.
  - It's similar to `@mgi`, however with manual explicit matching. May contradict the inference of active strategy maching

For attributes (when a feature have attributes added or changed from the original)
- `@msa`: metadata of source of an attribute.

<!--

```
@mas=opening_hours@(=@did=1@fid=2345|~@did=4@fid=1357)$@fee@(..)$ref:vatin@(...)
Explanation= 
> tag opening_hours
> Igual @tid=2345 (arquivo fonte 1)
> Muito semelhante, mas não idêntico @fid=1357 do @did=4
> tag fee ...
> tag ref:vatin
```
or

@mas=opening_hours@(=1:2345|~=4:1357)$@fee@(..)$ref:vatin@(...)
Explanation= 
> tag opening_hours
> strict same as @fid=2345 from dataset @did=1)
> Muito semelhante, mas não idêntico @fid=1357 do @did=4
> tag fee ...
> tag ref:vatin
```

-->

each feature is calculated, and the ones with the same group are considered be from the same group

All features with same code are considered to be in the same group ()

<!--

@TODO implement these shortcuts to create implicit queries to match objects


## MS "Match Strategy"
### For strict strategy, terms after 2nd // are keys, split by |
//MS//website

//MS//addr:street
//MS//addr:housenumber

//MS//addr:street|addr:housenumber|amenity
//MS//wikidata

### Specify target
...

### Other Ids

@tid
@fid

@did (original dataset Dataset ID)
@fid (original feature ID)
@mgi (pattern matching identifier group; e.g for standard strategy, perfect matches)

@mmi (manual matching / matches not following the standard procedure)

@mdi (matching duplicated id)

@mas (source from an attribute): syntax 
@mas=opening_hours@(=@did=1@fid=2345|~@did=4@fid=1357)$@fee@(..)$ref:vatin@(...)
Explanation= 
> tag opening_hours
> Igual @tid=2345 (arquivo fonte 1)
> Muito semelhante, mas não idêntico @fid=1357 do @did=4
> tag fee ...
> tag ref:vatin

## deploy

ssh://dh_ee2cqp@75.119.207.170/home/dh_ee2cqp/sdm.etica.ai/
ssh dh_ee2cqp@75.119.207.170:/home/dh_ee2cqp/sdm.etica.ai/
-->

## Quickstart to debug

1. Using the console of your browser, the variable `SDMData` will contain most of the underlining data of the memory (the v0.5.0 the close equivalent would be `WorkingData`). The `SDMConf` also contains some internal configurations and reference to some options defined by the user.

<!--


### Overview of data integration tasks
To contextualize data matching, let's divide Data integration from different in 3 big tasks:

1. Schema Matching -> 2. Data Matching -> 3. Data Fusion

**The SDM tool focuses on Data Matching, while providing some support to make easier encode
(e.g write instructions) to help with Schema Matching and Data Fusion.**

**Schema Maching** means that the dataset schema (e.g.
in simplistic terms the name of the fields and the formatting of the values of these fields)
needs to be aligned.
While the formatting and/or cleaning of values may be viable with some automation,
the decision making behind how attributes in one dataset align with another is a very human task.
It's recommended not only you explore the data in each dataset,
but (when available) the documentation explaining the fields of each dataset.

The **Data Maching** is the task of identifying and matching individual records from different datasets that refer to the same real-world entity.
Different levels of specificity between the datasets (e.g. not data errors,
but its schema, the different ontological ways to represent things and how detailed it is) may pose some challenges.
In some cases the point of view (think in the way the schema one dataset is organized) will consider items in other dataset as duplicates or have no way to describe some of its information (such as one schema focused on places have no attributes to describe persons as an dedicated entity).

Finally, **Data Fusion** is the step of getting knowledge back from the result of Data Matching. Unless the intent is to create a composite work with several sources,
this means merge (or do additional steps to review, as far as go out and visit the place to confirm the ground truth) information into one of the source providers of the dataset already focused in the previous step.


-->