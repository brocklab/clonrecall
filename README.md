# ClonRecall: ClonMapper Recall Utility

## Why?

Manually editing DNA sequences is error prone and tedious.
This script is designed to quickly generate the necessary oligos and plasmid vectors for any specified ClonMapper barcode.

## Setup

Only requirement is `python3`.

Start by cloning the repo.

```bash
git clone git@github.com:brocklab/clonrecall.git
cd clonrecall
```

## Usage

There are two commands for `clonrecall` each has essentially the same sets of flags to control behavior.

For each command you need to specify a 20bp barcode sequence and a name. You may also provide a headerless csv with multiple barcodes.

example csv:
```bash
lin1,GCAATATGCGGTACGATTCG
lin2,ACGGGTAGACCATACGATGC
```

### Oligos

To generate all six oligos which will be used to generate the recall plasmid you can use something like the below command:
```bash
./clonrecall oligo -s GCAATATGCGGTACGATTCG -n lin1
```

By default the oligos command will print the comma separated sequences to `stdout`.
These can be directly copied and pasted into IDT's bulk input.

You may also specify and output file with `-o/--output`.

### Plasmids

Similarly you can generate an annotated recall vector with a 3x barcode array.
In this case `-o/--output` is specifying a directory to save all generated `.gb` files.

```bash
./clonrecall plasmid -s ACGGGTAGACCATACGATGC -n lin2 -o recall-vectors
```
