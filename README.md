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

- `rbh` - contains a unique identifier for this file. Used to trace back to this line from downstream analyses. Do not leave this field blank.
- `gene_group` - Usually used to mark an ALG.
- `color` - Used to plot this line. Format is a hex color, like "#B07DF4". If there is no color, use black, "#000000", or nothing, "".

Each sample that is present in the file has five columns. Sample names cannot have underscore characters, `_`, as this character is used to delimit the fields. Each samplename must be unique. In the example below, we use the string "sampleName" to denote one sample --- this string will be 
- `sampleName_scaf`
- `sampleName_gene`
- `sampleName_strand`
- `sampleName_start`
- `sampleName_stop`


```
rbh     gene_group      color   BCnSSimakov2022_gene    BCnSSimakov2022_scaf    BCnSSimakov2022_pos
Simakov2022BCnS_genefamily_10069        C1      #B07DF4 Simakov2022BCnS_genefamily_10069        C1      1       TWW79076.1      CM011078.1      1097092
Simakov2022BCnS_genefamily_10079        C1      #B07DF4 Simakov2022BCnS_genefamily_10079        C1      2       TWW74641.1      CM011082.1      6561482
Simakov2022BCnS_genefamily_1011 C1      #B07DF4 Simakov2022BCnS_genefamily_1011 C1      3       TWW57762.1      CM011075.1      6318444
Simakov2022BCnS_genefamily_10152        C1      #B07DF4 Simakov2022BCnS_genefamily_10152        C1      4       TWW57729.1      CM011075.1      5736894
Simakov2022BCnS_genefamily_10297        C1      #B07DF4 Simakov2022BCnS_genefamily_10297        C1      5       TWW56077.1      CM011076.1      665820
Simakov2022BCnS_genefamily_10366        C1      #B07DF4 Simakov2022BCnS_genefamily_10366        C1      6       TWW66613.1      CM011088.1      7272376
Simakov2022BCnS_genefamily_10467        C1      #B07DF4 Simakov2022BCnS_genefamily_10467        C1      7       TWW77815.1      CM011080.1      14814994
Simakov2022BCnS_genefamily_10532        C1      #B07DF4 Simakov2022BCnS_genefamily_10532        C1      8       TWW57960.1      CM011075.1      9085640
```
