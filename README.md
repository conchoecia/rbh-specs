# rbh-specs
These documents are the specifications for the `rbh` file formats used by the [odp](https://github.com/conchoecia/odp) software.

The `rbh` file formats encode orthologies of genomic coordinates. There are two versions of `rbh` file currently in circulation.
The version:
  - `rbh` is the original format that, for each sample for which an orthology is tracked, contains information about the ortholog's scaffold, position, and gene name.
  - `rbh2` is the new format that encodes the same information as above, but also tracks the strand, and the start/stop position of the feature rather than a generic position coordinate.

## General description

The `rbh` file format was designed with flexibility in mind. In a typical bioinformatics file format, the contents of each column are rigidly specified by their index, and the number of columns in the file must match the specifications. The `rbh` file format, instead, uses named column headers to determine the column contents. There is a minimum set of columns which must exist for a `rbh` file, and additional columns can be added at the user's discretion based on their needs. The specifications for the original `rbh` and the new `rbh2` are below.

## File Format Specifications - `rbh`

See the [odp](https://github.com/conchoecia/odp) documents.

## File Format Specifications - `rbh2`

Every `rbh2` file must have the following columns. We recommend that these columns are printed to the file first.
