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

Each sample that is present in the file has five columns. Sample names cannot have underscore characters, `_`, as this character is used to delimit the fields. Each samplename must be unique. In the example below, we use the string "sampleName" to denote one sample --- this string will be changed for every sample encoded in the genome.
- `sampleName_scaf` - Contains the scaffold name (fasta header) on which this locus exists. This must be an exact match of a scaffold name fasta header found in the source genome fasta file.
- `sampleName_gene` - If a protein, this is the fasta header of this protein fasta entry for this ortholog, and must exactly match a protein name in the fasta header. If not a protein, must have some other name unique to this column for this orthology file.
- `sampleName_strand` - Must be '+' or '-' if the strand of the feature is known. Must be the '.' character if the strand is not known/relevant. If a protein, must be the encoding strand relative to the genome fasta file. If extracted from a .maf file, takes the strand from the alignment.
- `sampleName_start` - The left-most position of this feature. Uses bed-format numbering conventions. From Wikipedia, this column 'chromStart' is defined as: "Start coordinate on the chromosome or scaffold for the sequence considered (the first base on the chromosome is numbered 0 i.e. the number is zero-based)". This value will always be less than the value of `sampleName_stop`.
- `sampleName_stop` - The right-most position of this feature. Uses bed-format numbering conventions. From Wikipedia, this column 'chromEnd' is defined as: "End coordinate on the chromosome or scaffold for the sequence considered. This position is non-inclusive, unlike chromStart (the first base on the chromosome is numbered 1 i.e. the number is one-based)." This value will always be greater than the value of `sampleName_start`.
