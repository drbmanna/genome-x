# Data

Data files are not committed to this repository. Download them into this `data/` folder by
following the notes below. The `.gitignore` keeps everything here out of Git except this
file.

## What we need

CTCF binding data for K562 cells from the ENCODE Project, plus the matching reference genome
sequence.

- CTCF ChIP-seq peaks for K562: the regions where CTCF was found bound. These are the
  positive examples.
- A reference genome sequence (the genome build must match the peak file). This is used to
  read the DNA letters at each region.

Find the files on the ENCODE portal: https://www.encodeproject.org

## Before you download, decide and write down

- The exact ENCODE accession(s) you chose.
- The genome build (for example GRCh38 / hg38). The peaks and the genome sequence must use
  the same build, or the coordinates will not line up.
- What the labels mean in the file you picked.

## Record for every download (fill this in)

Keeping this record is how the project stays reproducible. Do not skip it.

| Item | Value |
|------|-------|
| ENCODE accession(s) | |
| File type(s) | |
| Genome build | |
| Download date | |
| Download command / URL | |
| File size(s) | |
| Checksum (md5) | |

## Note on N

Some genome positions are the letter N, which means the base is unknown (an assembly gap or
masked region). N is not a mutation. Decide how to handle sequence windows that contain N
(for example, drop them) and record how many you dropped.

## The negative set (important)

ENCODE peaks give positive examples (bound). You must construct the negative examples (not
bound) yourself. How you choose them decides what the model actually learns. Random genome
regions differ from CTCF peaks in GC content, so a careless negative set lets the model
learn "GC content" instead of the CTCF pattern. Decide and document your negative-set method
before training.
