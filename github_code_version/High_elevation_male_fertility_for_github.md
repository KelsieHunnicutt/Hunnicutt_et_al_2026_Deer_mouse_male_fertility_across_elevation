```
# download data from SRA to a directory called:

mkdir spermoxia

# download data to
mkdir 01.RawData
```

# pre-processing (fastqc + trimmomatic)
```
#run fastqc before trimming;
if data is already unzipped, make sure to rezip originals after trimming
module load tools/fastqc/0.11.9 
mkdir spermoxia/fastqc_pre-trimm/sample_fqc-out/

cd 01.RawData/
gunzip sample_1.fq.gz
gunzip sample_2.fq.gz

#forward
fastqc -t 4 -o spermoxia/fastqc_pre-trimm/sample_fqc-out/ \
-f fastq 01.RawData/sample_1.fq

#reverse
fastqc -t 4 -o spermoxia/fastqc_pre-trimm/sample_fqc-out/ \
-f fastq 01.RawData/sample_2.fq

# rezip
gzip sample_1.fq
gzip sample_2.fq
```

## trimmomatic then fastqc post-trimm
```
mkdir -p spermoxia/post-trimm/
mkdir -p spermoxia/post-trimm/trimm-logs
mkdir -p spermoxia/post-trimm/fastqc_post-trimm
```

```
#general paired trimmomatic and post-trimm fastqc
module load tools/fastqc/0.11.9 
module load tools/trimmomatic/0.39

# run trimmomatic
java -jar /cm/shared/tools/trimmomatic/0.39/trimmomatic-0.39.jar PE -threads 8 -phred33 \
-trimlog spermoxia/post-trimm/trimm-logs/sample_trimm.log \
01.RawData/sample/sample_1.fq 01.RawData/sample/sample_2.fq \
spermoxia/post-trimm/paired/sample_1.paired.fq.gz \
spermoxia/post-trimm/unpaired/sample_1.unpaired.fq.gz \
spermoxia/post-trimm/paired/sample_2.paired.fq.gz  \
spermoxia/post-trimm/unpaired/sample_2.unpaired.fq.gz \
ILLUMINACLIP:/path/to/adapters/TruSeq3-PE.fa:2:30:10 LEADING:5 TRAILING:5 SLIDINGWINDOW:4:15 MINLEN:36

date 
mkdir spermoxia/post-trimm/fastqc_post-trimm/sample_fqc-out/

# ungzip the paired trimmed reads, run trimmomatic, and regzip
gunzip spermoxia/post-trimm/paired/sample_1.paired.fq.gz
fastqc -t 8 -o spermoxia/post-trimm/fastqc_post-trimm/sample_fqc-out/ \
-f fastq spermoxia/post-trimm/paired/sample_1.paired.fq
gzip spermoxia/post-trimm/paired/sample_1.paired.fq

gunzip spermoxia/post-trimm/paired/sample_2.paired.fq.gz
fastqc -t 8 -o spermoxia/post-trimm/fastqc_post-trimm/sample_fqc-out/ \
-f fastq spermoxia/post-trimm/paired/sample_2.paired.fq
gzip spermoxia/post-trimm/paired/sample_2.paired.fq
```


# star analysis
## index genome
```
# recommended to do in an empty folder
cpu=16
ref_dir=spermoxia/genome_links/pman-2025_star
ref=spermoxia/genome_links/pman-2025_star/pman-2025_genome.fna
ref_gtf=spermoxia/genome_links/GCF_049852395.1_HU_Pman_BW_mat_3.1_annotation.gtf

conda activate star

cd ${ref_dir}

date

STAR \
--runThreadN ${cpu} \
--runMode genomeGenerate \
--genomeDir ${ref_dir} \
--genomeFastaFiles ${ref} \
--sjdbGTFfile ${ref_gtf}

date
```

## basic star run
```{bash}
# run star on chosen sample
ref_dir=spermoxia/genome_links/pman-2025_star
ref=spermoxia/genome_links/pman-2025_star/pman-2025_genome.fna
ref_gtf=spermoxia/genome_links/GCF_049852395.1_HU_Pman_BW_mat_3.1_annotation.gtf
base_dir=spermoxia/post-trimm/
cpu=16
read_base=spermoxia/post-trimm/paired
sample=example


mkdir -p ${base_dir}/post-star

conda activate star

cd ${base_dir}/post-star

date

STAR \
-- runMode alignReads \
--runThreadN ${cpu} \
--genomeDir ${ref_dir} \
--readFilesCommand zcat \
--readFilesIn ${read_base}/${sample}_1.paired.fq.gz ${read_base}/${sample}_2.paired.fq.gz \
--outFileNamePrefix ${sample}_ \
--outSAMtype BAM SortedByCoordinate \
--quantMode GeneCounts

date
```