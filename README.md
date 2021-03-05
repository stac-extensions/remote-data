# Remote Data (Example) Extension Specification

- **Title:** Remote Data (Example Extension)
- **Identifier:** <https://stac-extensions.github.io/remote-data/v1.0.0/schema.json>
- **Field Name Prefix:** rd
- **Scope:** Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @cholmes @matthewhanson

This is an example vendor extension for a fictional company "Remote Data". It is used in some of the examples provided in the STAC spec.

Remote Data wants to use STAC for their satellite and airborne data, but have additional fields they would want their STAC Items to include.
To allow the new fields to be properly documented and validated, Remote Data creates a STAC Extension to store these additional fields, following
the process for creating any other extension. A README (this file) to describe the purpose and fields, example metadata, and a JSON Schema.

- Examples:
  - [Item example](examples/item.json): Shows the basic usage of the extension in a STAC Item
  - [Collection example](examples/collection.json): Shows the basic usage of the extension in a STAC Collection
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Item Properties

| Field Name           | Type                      | Description |
| -------------------- | ------------------------- | ----------- |
| rd:type        | string                    | **REQUIRED**. The type of data, currently only "scene" is supported |
| rd:product_level | string | **REQUIRED**. The processing level of the data. Must be one of LV1A, LV1B, LV2A, LV2B, LV3A, or LV3B |
| rd:sat_id  | string        | **REQUIRED**. The internal designation of a satellite (if satellite data) |
| rd:runs    | \[string]     | A string list of names names for each model run associated with this scene |
| rd:parsecs | \[number]     | A list of the parsecs for each run in rd:runs |
| rd:anomalous_pixels | number | A number between 0-1 indicating the fraction of anamalous pixels in the scene |
| rd:earth_sun_distance | number | The distance between the earth and the sun at the time of collect, defined in [Astronomical Units](https://en.wikipedia.org/wiki/Astronomical_unit) |
| rd:flux_capacitor | boolean | Indicates if the flux capacitor was enabled during data collection. If not present, it indicates false |

## Collection Fields

| Field Name           | Type                      | Description |
| -------------------- | ------------------------- | ----------- |
| rd:visibility        | string                    | **REQUIRED**. Visibility of the collection. Must be one of `public`, `protected`, or `private` |
