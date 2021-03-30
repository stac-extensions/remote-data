# Remote Data (Example) Extension Specification

- **Title:** Remote Data (Example Extension)
- **Identifier:** <https://stac-extensions.github.io/remote-data/v1.0.0/schema.json>
- **Field Name Prefix:** rd
- **Scope:** Item, Collection
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @cholmes @matthewhanson

This is an example vendor extension for a fictional company "Remote Data". It is used in some of the examples provided in the
[SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

Fictional use case:
Remote Data wants to use STAC for their satellite and airborne data, but have additional fields they would want their STAC Items to include.
To allow the new fields to be properly documented and validated, Remote Data creates a STAC Extension to store these additional fields, following
the process for creating any other extension. A README (this file) to describe the purpose and fields, example metadata, and a JSON Schema.

- Examples:
  - [Item example](examples/item.json): Shows the basic usage of the extension in a STAC Item
  - [Collection example](examples/collection.json): Shows the basic usage of the extension in a STAC Collection
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Item Properties

| Field Name            | Type      | Description                                                  |
| --------------------- | --------- | ------------------------------------------------------------ |
| rd:type               | string    | **REQUIRED**. The type of data, currently only "scene" is supported |
| rd:product_level      | string    | **REQUIRED**. The processing level of the data. Must be one of LV1A, LV1B, LV2A, LV2B, LV3A, or LV3B |
| rd:sat_id             | string    | **REQUIRED**. The internal designation of a satellite (if satellite data) |
| rd:runs               | \[string] | A string list of names names for each model run associated with this scene |
| rd:parsecs            | \[number] | A list of the parsecs for each run in rd:runs                |
| rd:anomalous_pixels   | number    | A number between 0-1 indicating the fraction of anamalous pixels in the scene |
| rd:earth_sun_distance | number    | The distance between the earth and the sun at the time of collect, defined in [Astronomical Units](https://en.wikipedia.org/wiki/Astronomical_unit) |
| rd:flux_capacitor     | boolean   | Indicates if the flux capacitor was enabled during data collection. If not present, it indicates false |

## Collection Fields

| Field Name           | Type                      | Description |
| -------------------- | ------------------------- | ----------- |
| rd:visibility        | string                    | **REQUIRED**. Visibility of the collection. Must be one of `public`, `protected`, or `private` |

## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid. 
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on 
your command line run:
```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:
```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:
```bash
npm run format-examples
```
