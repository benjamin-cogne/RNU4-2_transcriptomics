# Code used for RNU4-2 transcriptomics analysis
Paired-end fastq files have previously been aligned on GRCh38 using STAR 2.7.11a:

~~~
STAR-avx --runThreadN 12 --genomeDir genomeDir_grch38/ --readFilesIn 1.fastq.gz 2.fastq.gz --outSAMtype BAM SortedByCoordinate --chimSegmentMin 20 --twopassMode Basic --outFileNamePrefix prefix --readFilesCommand zcat --outSAMunmapped Within --outSAMattrRGline ID:4 LB:rnaseq-capture PL:ILLUMINA SM:20 PU:unit1 --outTmpDir tmp --quantMode GeneCounts
~~~

Rmats was then run on aligned BAM files using:
~~~
python rmats.py --gtf currentHomo_sapiens.GRCh38.106.gtf --tmp /data1/tmp --readLength 76 --b1 b1.txt --b2 b2.txt --od results -t paired --anchorLength 1 --nthread 5 --libType fr-firststrand --task both --novelSS --variable-read-length --allow-clipping
~~~

The jupyter notebooks in this github are used to filter and plot PCA to visualize splicing signatures. It also has code used to plot spliceAI scores and consensus sequences.

