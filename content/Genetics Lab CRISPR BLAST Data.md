```
LOCUS       CP157234             4940562 bp    DNA     circular BCT 02-JUN-2024
DEFINITION  Escherichia coli strain 2024CK-00474 chromosome, complete genome.
ACCESSION   CP157234 ABRXZK010000000 ABRXZK010000001-ABRXZK010000132
VERSION     CP157234.1
DBLINK      BioProject: [PRJNA812595](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA812595)
            BioSample: [SAMN41094955](https://www.ncbi.nlm.nih.gov/biosample/SAMN41094955)
KEYWORDS    .
SOURCE      Escherichia coli
  ORGANISM  [Escherichia coli](https://www.ncbi.nlm.nih.gov/Taxonomy/Browser/wwwtax.cgi?id=562)
            Bacteria; Pseudomonadota; Gammaproteobacteria; Enterobacterales;
            Enterobacteriaceae; Escherichia.
REFERENCE   1  (bases 1 to 4940562)
  AUTHORS   Hergert,J., Casey,R., Wagner,J., Young,E.L. and Oakeson,K.F.
  TITLE     Pathogen: clinical or host-associated sample
  JOURNAL   Unpublished
REFERENCE   2  (bases 1 to 4940562)
  CONSRTM   Clinical and Environmental Microbiology Branch: Whole genome
            sequencing antimicrobial resistance pathogens in the healthcare
            setting
  TITLE     Direct Submission
  JOURNAL   Submitted (26-APR-2024) Division of Healthcare Quality Promotion,
            US Centers for Disease Control and Prevention, 1600 Clifton Rd,
            Atlanta, GA, USA
REFERENCE   3  (bases 1 to 4940562)
  AUTHORS   Hergert,J., Casey,R., Wagner,J., Young,E.L. and Oakeson,K.F.
  TITLE     Direct Submission
  JOURNAL   Submitted (21-MAY-2024) Utah Public Health Laboratory, Utah Public
            Health Laboratory Infectious Disease submission group, 4431 S 2700
            W, Salt Lake City, UT 84129, USA
COMMENT     The annotation was added by the NCBI Prokaryotic Genome Annotation
            Pipeline (PGAP). Information about PGAP can be found here:
            [https://www.ncbi.nlm.nih.gov/genome/annotation_prok/](https://www.ncbi.nlm.nih.gov/genome/annotation_prok/)
            
            ##Genome-Assembly-Data-START##
            Assembly Method        :: Unicycler v. 0.5.0
            Genome Representation  :: Full
            Expected Final Version :: Yes
            Genome Coverage        :: 50.0x
            Sequencing Technology  :: Illumina MiSeq; Oxford Nanopore GridION
            ##Genome-Assembly-Data-END##
            
            ##Genome-Annotation-Data-START##
            Annotation Provider               :: NCBI
            Annotation Date                   :: 05/24/2024 09:43:26
            Annotation Pipeline               :: NCBI Prokaryotic Genome
                                                 Annotation Pipeline (PGAP)
            Annotation Method                 :: Best-placed reference protein
                                                 set; GeneMarkS-2+
            Annotation Software revision      :: 6.7
            Features Annotated                :: Gene; CDS; rRNA; tRNA; ncRNA
            Genes (total)                     :: 5,073
            CDSs (total)                      :: 4,953
            Genes (coding)                    :: 4,699
            CDSs (with protein)               :: 4,699
            Genes (RNA)                       :: 120
            rRNAs                             :: 8, 7, 7 (5S, 16S, 23S)
            complete rRNAs                    :: 8, 7, 7 (5S, 16S, 23S)
            tRNAs                             :: 91
            ncRNAs                            :: 7
            Pseudo Genes (total)              :: 254
            CDSs (without protein)            :: 254
            Pseudo Genes (ambiguous residues) :: 0 of 254
            Pseudo Genes (frameshifted)       :: 77 of 254
            Pseudo Genes (incomplete)         :: 163 of 254
            Pseudo Genes (internal stop)      :: 51 of 254
            Pseudo Genes (multiple problems)  :: 32 of 254
            CRISPR Arrays                     :: 3
            ##Genome-Annotation-Data-END##
```

```
  [gene](https://www.ncbi.nlm.nih.gov/nuccore/CP157234.1?from=448252&to=448626)            448252..448626
                     /gene="rpsL"
                     /locus_tag="ABI159_02050"     
[CDS](https://www.ncbi.nlm.nih.gov/nuccore/CP157234.1?from=448252&to=448626)             448252..448626
                     /gene="rpsL"
                     /locus_tag="ABI159_02050"
                     /inference="COORDINATES: similar to AA
                     sequence:RefSeq:WP_005306278.1"
                     /note="Derived by automated computational analysis using
                     gene prediction method: Protein Homology.
                     GO_component: [GO:0000314 - organellar small ribosomal](http://amigo.geneontology.org/amigo/term/GO:0000314)
                     [subunit](http://amigo.geneontology.org/amigo/term/GO:0000314) [Evidence IEA];
                     GO_component: [GO:0022627 - cytosolic small ribosomal](http://amigo.geneontology.org/amigo/term/GO:0022627)
                     [subunit](http://amigo.geneontology.org/amigo/term/GO:0022627) [Evidence IEA];
                     GO_function: [GO:0003735 - structural constituent of](http://amigo.geneontology.org/amigo/term/GO:0003735)
                     [ribosome](http://amigo.geneontology.org/amigo/term/GO:0003735) [Evidence IEA];
                     GO_process: [GO:0006412 - translation](http://amigo.geneontology.org/amigo/term/GO:0006412) [Evidence IEA]"
                     /codon_start=1
                     /transl_table=[11](https://www.ncbi.nlm.nih.gov/Taxonomy/Utils/wprintgc.cgi?mode=c#SG11)
                     /product="30S ribosomal protein S12"
                     /protein_id="[XBJ68103.1](https://www.ncbi.nlm.nih.gov/protein/2738661255)"
                     /translation="MATVNQLVRKPRARKVAKSNVPALEACPQKRGVCTRVYTTTPKK
                     PNSALRKVCRVRLTNGFEVTSYIGGEGHNLQEHSVILIRGGRVKDLPGVRYHTVRGAL
                     DCSGVKDRKQARSKYGVKRPKA"
                     
FEATURES             Location/Qualifiers
     source          1..4940562
                     /organism="Escherichia coli"
                     /mol_type="genomic DNA"
                     /strain="2024CK-00474"
                     /isolation_source="urine"
                     /host="Homo sapiens"
                     /db_xref="taxon:[562](https://www.ncbi.nlm.nih.gov/Taxonomy/Browser/wwwtax.cgi?id=562)"
                     /geo_loc_name="USA"
                     /collection_date="2024-02-20"
```


WT: 
```
TTAAGCCTTAGGACGCTTCACGCCATACTTGGAACGAGCCTGCTTACGGTCTTTAACGCCGGAGCAGTCAAGCGCACCACGTACGGTGTGGTAACGAACACCCGGGAGGTCTTTAACACGACCGCCACGGATCAGGATCACGGAGTGCTCCTGCAGGTTGTGACCTTCACCACCGATGTAGGAAGTCACTTCGAAACCGTTAGTCAGACGAACACGGCATACTTTACGCAGCGCGGAGTTCGGTTTTTTAGGAGTGGTAGTATATACACGAGTACATACGCCACGTTTTTGCGGGCATGCTTCCAGCGCAGGCACGTTGCTTTTCGCAACTTTGCGAGCACGTGGTTTGCGTACCAGCTGGTTAACTGTTGCCAT
```

Edited: 
```
TTAAGCCTTAGGACGCTTCACGCCATACTTGGAACGAGCCTGCTTACGGTCTTTAACGCCGGAGCAGTCAAGCGCACCACGTACGGTGTGGTAACGAACACCCGGGAGGTCTTTAACACGACCGCCACGGATCAGGATCACGGAGTGCTCCTGCAGGTTGTGACCTTCACCACCGATGTAGGAAGTCACTTCGAAACCGTTAGTCAGACGAACACGGCATACTTTACGCAGCGCGGAGTTCGGTTTTGTAGGAGTGGTAGTATATACACGAGTACATACGCCACGTTTTTGCGGGCATGCTTCCAGCGCAGGCACGTTGCTTTTCGCAACTTTGCGAGCACGTGGTTTGCGTACCAGCTGGTTAACTGTTGCCAT
```



Comparison

![[Pasted image 20240913134803.png]]
