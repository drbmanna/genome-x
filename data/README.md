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
| ENCODE accession(s) | ENCFF016NHU, ENCFF020ZZK, ENCFF041ODC, ENCFF042WXA, ENCFF044KHD, ENCFF075EWP, ENCFF089FZZ, ENCFF090ZJH, ENCFF100SVR, ENCFF101MTI, ENCFF119XFJ, ENCFF142QQP, ENCFF153CDM, ENCFF175EOP, ENCFF179UDP, ENCFF221SKA, ENCFF233NBA, ENCFF248VAH, ENCFF327LCP, ENCFF329ZKC, ENCFF349NJE, ENCFF362OPG, ENCFF374VTS, ENCFF389ELU, ENCFF396BZQ, ENCFF406IQL, ENCFF447AYX, ENCFF459FPS, ENCFF479VOH, ENCFF479WBH, ENCFF495HCX, ENCFF500NYB, ENCFF503KGE, ENCFF519CXF, ENCFF569NFY, ENCFF582SNT, ENCFF618RCT, ENCFF660GHM, ENCFF667VJC, ENCFF680NXZ, ENCFF694KDC, ENCFF697VGB, ENCFF712ETC, ENCFF736NYC, ENCFF740TLU, ENCFF748CZJ, ENCFF764CER, ENCFF769AUF, ENCFF770ZIZ, ENCFF778KEG, ENCFF788RSH, ENCFF792OOT, ENCFF822CTO, ENCFF843VHC, ENCFF871HJT, ENCFF873LHT, ENCFF876IUR, ENCFF878XBH, ENCFF882NGM, ENCFF895WIT, ENCFF901CBP, ENCFF933UDR, ENCFF942DXM, ENCFF973WXW, ENCFF976ZJD |
| File type(s) | gz, txt |
| Genome build | hg38 |
| Download date | October 19, 2026 |
| Download command / URL | Tracked in data/files.txt (67 files total) |
| File size(s) | 0.14 GB total |
| Checksum (md5) | Verified via data/files.txt manifest |
|------|-------|



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
