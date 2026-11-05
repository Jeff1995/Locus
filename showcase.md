# Locus showcase

Open this note in a vault with Locus enabled to see every feature, in both reading view and live preview.

## Headings share one lightness

### Level three
#### Level four
#### Another level four
##### Level five
###### Level six

### Numbering continues

The headings above read 1, 1.1, 1.1.1, 1.1.2, 1.1.2.1, 1.1.2.1.1; this one is 1.2.

Peaks were called with `macs2 callpeak -f BEDPE` on [[pseudobulk fragments]]; see the [ENCODE blacklist](https://github.com/Boyle-Lab/Blacklist). Tagged #proj/example #labmeeting. ==FRiP below 0.2 was excluded.== **Bold** and *italic*.

> Chromatin accessibility is a proxy, not a measurement, of TF occupancy.

Inline math $\log_2 \mathrm{FC} = \log_2(\mu_1 / \mu_0)$ is not numbered; display math is:

$$
\text{TSS enrichment} = \frac{\max_{x \in [-50, 50]} \text{cov}(x)}{\text{mean}(\text{cov}_{\pm 1.9\text{–}2\,\text{kb}})}
$$

$$
y = X\beta + \varepsilon
$$

## Task states

- [ ] Re-run ArchR with tile size 500 bp
- [x] Download GSE123456 fragments
- [>] Forwarded: email core about NovaSeq slot
- [<] Scheduled: lab meeting slides
- [-] Cancelled: try MACS2 broad peaks
- [/] In progress: chromVAR deviations
- [?] Why is TSS enrichment low in batch 3?
- [!] Important: IRB renewal due Friday
- [i] Info: Tn5 lot changed on 10/12
- [I] Idea: footprint with PRINT on bulk
- [*] Starred
- [b] Bookmarked

With the Tasks plugin, open tasks that are overdue or due today are flagged:

- [ ] Overdue example 📅 2020-01-01
- [ ] Future example 📅 2099-01-01

```tasks
path includes showcase
not done
```

## Callouts

> [!method] Method
> Tn5 tagmentation, 50k nuclei, 30 min at 37 °C.

> [!result] Result
> Median TSS enrichment 14.2 (IQR 11.8–16.5).

> [!hypothesis]
> GATA motifs gain accessibility before lineage commitment.

> [!dataset]
> GSE123456: 12 donors, 84,301 cells.

> [!cmd] Command
> `snakemake -j 64 --use-conda`

> [!figure] Figure 2
> UMAP colored by donor; batch 3 separates on PC2.

> [!paper]
> Buenrostro et al. 2013, *Nat Methods* 10:1213.

> [!caveat]
> Doublets were not removed for donor 7.

> [!primer] Nextera read 1
> TCGTCGGCAGCGTCAGATGTGTATAAGAGACAG

> [!meeting] Lab meeting
> Discussed peak-calling thresholds.

> [!ai]
> Summary drafted by an assistant.

> [!tip]
> Built-in callouts are recolored too.

> [!warning]
> As is warning.

## Table

| Sample   | Cells  | Median frags | TSS enr. | FRiP |
| -------- | -----: | -----------: | -------: | ---: |
| donor_01 |  7,412 |       18,204 |     14.2 | 0.41 |
| donor_02 | 11,087 |        9,876 |     11.8 | 0.33 |
| donor_03 |    903 |       21,553 |     16.5 | 0.18 |

## Code

```python
import scanpy as sc

# filter low-quality cells
adata = sc.read_h5ad("atac.h5ad")
adata = adata[adata.obs["tss_enrichment"] > 4]
```

```r
library(ArchR)
proj <- addIterativeLSI(proj, useMatrix = "TileMatrix", iterations = 2)
```

```bash
bedtools intersect -a peaks.bed -b blacklist.bed -v > peaks.filtered.bed
```

```fasta
>chr1:1000-1200
ACGTTGCATGCATGCATCGATCGATCGTAGCTAGCTAGCTAGCATCGATCGATCGATCGATCGTAGCTAGCTAGCTAGCTAGCATCGATCGATCGATCGATCGATCGTAGCTAGCTAGCTAGCTAGCATCGATCGATCGATCGATCGATCGATCG
```

```vcf
#CHROM	POS	ID	REF	ALT	QUAL	FILTER	INFO
chr1	10177	rs367896724	A	AC	100	PASS	AC=2130;AF=0.425319;AN=5008;NS=2504;DP=103152
chr1	10235	rs540431307	T	TA	100	PASS	AC=6;AF=0.00119808;AN=5008;NS=2504;DP=78015
```
