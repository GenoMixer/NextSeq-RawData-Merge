# NextSeq-RawData-Merge
Workflow for merging multi-lane fastq files from the Illumina NextSeq 550 using Snakemake. In addition, basic QC is applied and md5 checksums are generated.

## Requirement
- Unix (tested on Debian)
- Snakemake
- Python 3.5+
- FastQC and MultiQC

## Directory Structure
When a NextSeq 550 sequencing run is completed the FASTQ files are located in "<run folder>\Alignment_1\<subfolder>\Fastq". For each sample the sequencer generates fastq files for each lane and read orientation. The format in which the fastq file are stored looks like this ("*_L00[1-4]_R[1-2]_001.fastq.gz"). After merging the lane information is discarded from the sample name.

221127_NB442557_0103_AH4v22BGXN  \
└──SampleSheet.csv  \
└── Alignment_1    \
&nbsp;&nbsp; └── 20221215_184340   \
&nbsp;&nbsp;&nbsp;&nbsp; └── Fastq
        
## Usage

1. Clone the repository:

    ```bash
    git clone https://github.com/GenoMixer/NextSeq-RawData-Merge.git
    ```

2. Activate the snakemake environemnt with FastQC and MultiQC:

    ```bash
    conda activate snakemake
    ```

3. Start a dry run (-n) and estimate the numbers of jobs provided by snakemake:

    ```bash
    snakemake -n
    ```

4. Start real execution with estimated numbers of jobs that can be run in parallel (-j XXX):

    ```bash
    snakemake -j XXX 
    ```
