## Part II: Bioinfomratics on the Tufts HPC: tools, workflows, and available resources



Author: Shirley Li, xue.li37@tufts.edu

Date: 2025-10-02



## 1. Prerequisites

- Basic understanding of biology and bioinformatics

  - Familiarity with common bioinformatics data formats, including [FASTQ](https://knowledge.illumina.com/software/general/software-general-reference_material-list/000002211), [FASTA](https://pacbiofileformats.readthedocs.io/en/11.0/FASTA.html), [SAM](https://samtools.github.io/hts-specs/SAMv1.pdf), [BAM](https://support.illumina.com/help/BS_App_RNASeq_Alignment_OLH_1000000006112/Content/Source/Informatics/BAM-Format.htm), and [GTF files](https://useast.ensembl.org/info/website/upload/gff.html).

- [Familiarity with the command line](https://tuftsdatalab.github.io/tuftsWorkshops/2024_workshops/2024_bioinformatics201/linux/00_overview/)

- [Access to an HPC cluster](https://it.tufts.edu/researchtechnology.tufts.edu) (e.g., login credentials, necessary software installations)

## 2. Bioinformatics modules

### On the cluster

Use `module avail` to check the full list of tools available on the cluster. Below are some commonly used tools:

```
   abcreg/0.1.0                         kallisto/0.48.0                     (D)    orthofinder/2.5.5
   abyss/2.3.7                          kneaddata/0.12.0                           pandaseq/2.11
   alphafold/2.3.0                      kraken2/2.1.3                              parabricks/4.0.0-1
   alphafold/2.3.1                      krakentools/1.2                            parabricks/4.2.1-1
   alphafold/2.3.2                      macs2/2.2.7.1
   amplify/2.0.0                        macs3/3.0.0a6                              pepper_deepvariant/r0.8
   angsd/0.939                          masurca/4.0.9                              petitefinder/cpu
   angsd/0.940                   (D)    masurca/4.1.0                       (D)    picard/2.25.1
   bakta/1.9.3                          medaka/1.11.1                              picard/2.26.10
   bbmap/38.93                          megahit/1.2.9                              plink/1.90b6.21
   bbmap/38.96                   (D)    meme/5.5.5                                 plink2/2.00a2.3
   bbtools/39.00                        metaphlan/4.0.2                            polypolish/0.5.0
   bcftools/1.13                        metaphlan/4.0.6                     (D)    preseq/3.2.0
   bcftools/1.14                        miniasm/0.3_r179                           prokka/1.14.6
   bcftools/1.17                        minimap2/2.26                       (D)    qiime2/2023.2
   bcftools/1.20                 (D)    minipolish/0.1.3                           qiime2/2023.5
   beast2/2.6.3                         mirdeep2/2.0.1.3                           qiime2/2023.7
   beast2/2.6.4                         mirge3/0.1.4                               qiime2/2023.9
   beast2/2.6.6                  (D)    mothur/1.46.0                              qiime2/2024.2
   ... ...

```

### A few tips

1. Before installing your own tools, check if they are already available on the cluster using the `module avail` command.

1. Always be aware of the software versions, especially when using scripts from colleagues.

1. For less common tools, consider installing them yourself to ensure you have full control over the version and availability.

   **If you need to install a less commonly used tool, it's best to handle the installation yourself to ensure proper maintenance. Follow [this tutorial](https://tuftsdatalab.github.io/tuftsWorkshops/2024_workshops/2024_bioinformatics301/01_source/) to install your own tool**

## 3. Using the Open OnDemand App

* The current Open OnDemand server is available at [https://ondemand.pax.tufts.edu/](https://ondemand.pax.tufts.edu/)
* If your account has access to the new cluster, use the [new Open OnDemand server](http://ondemand-prod.pax.tufts.edu)
* To request access to the new cluster, complete the [early adopter program form](https://tufts.qualtrics.com/jfe/form/SV_08IS0n1YSTR6KRU)
* Additional information is available in the [New Cluster Guide](https://rtguides.it.tufts.edu/hpc/examples/new-cluster.html) 
* **In today’s workshop, I will demonstrate the features on the new OOD server.**


### RStudio Server

When launching RStudio Server, use **R/4.5.1**, which includes the most comprehensive set of pre-installed packages (1300+).

**How to launch RStudio on Open OnDemand**:

1. Log in to [new Open OnDemand server](http://ondemand-prod.pax.tufts.edu) 
   * Make sure you request access through the [early adopter program](https://tufts.qualtrics.com/jfe/form/SV_08IS0n1YSTR6KRU)
1. Navigate to `interactive apps` and select `RStudio Server`
1. Specify the required resources:
   - **Number of hours** 
     - **2 hours** → usually enough for testing or small jobs.
     - **8–12 hours** → good if you plan to work for most of the day and don’t need to continue the same session tomorrow.
     - For longer runs, it’s often better to use **batch jobs** instead of keeping an interactive session open.
   - **Number of cores** 
     - 1 core is fine for most jobs, request more only if your code is **parallelized**
   - **Amount of memory** 
     - 4-8Gb is good starting point
     - Requesting more memory often means longer wait times in the queue
   - **Partition** (set to `batch`)
   - **R version** (latest available: 4.5.1)
1. Click `Launch` to submit your job to the queue.
1. Wait a few minutes until your job starts running.
1. Click `Connect to Rstudio server`
1. In RStudio, go to the `Packages` tab on the right to check the installed packages.

**Installing R Packages**

Refer to our [previous workshop materials](https://tuftsdatalab.github.io/tuftsWorkshops/2024_workshops/2024_bioinformatics301/02_Rpackage/) for detailed instructions on installing R packages.



### Other Apps on OOD

In addition to RStudio, Open OnDemand provides several other applications to support your research:

- **Jupyter** – Python notebooks and interactive coding
- **Matlab Server** – run Matlab directly on the cluster
- **VS Code Server** – lightweight coding environment
- **FastQC** – sequence quality control
- **Fiji** – image analysis and visualization



### Ready-to-Use Genomics Pipelines (nf-core)

[nf-core pipelines](https://nf-co.re/pipelines) are community-developed, standardized workflows for common genomics tasks such as RNA-seq, variant calling, and methylation analysis.

* On the **new Open OnDemand server**, you can go to **nf-core pipelines** to see which pipelines are already installed.

* For step-by-step instructions, see the [Previous workshop on nextflow and nf-core](https://tuftsdatalab.github.io/tuftsWorkshops/2024_workshops/nfcore_rnaseq_sp24/00_introduction/).

  * [Slides](https://github.com/tuftsdatalab/tuftsWorkshops/tree/main/docs/2024_workshops/nfcore_rnaseq_sp24/slides)
  * [Hands-on](https://github.com/tuftsdatalab/tuftsWorkshops/blob/main/docs/2024_workshops/nfcore_rnaseq_sp24/02_rnaseq.md)
  

## 4. Writing a Bioinformatics Job Script

This section introduces how to write a SLURM job script for running bioinformatics workflows. The example uses **`nf-core/rnaseq`**, but the same structure applies to other tools, nf-core pipelines, and custom Nextflow workflows.

The **[nf-core](https://nf-co.re/)** community develops best-practice pipelines using **Nextflow**, a workflow manager for reproducible and scalable analyses across HPC, local, and cloud environments. The **[nf-core/rnaseq](https://nf-co.re/rnaseq/3.21.0/)** pipeline provides a complete solution for RNA-seq data processing, including quality control, alignment, and quantification.

### 4.1. Prepare the SLURM Script

Create a file named `run_nfcore_rnaseq.sh` and add the following content:

```
#!/bin/bash
#SBATCH -J RNASEQ_JOB           # Job name
#SBATCH --time=12:00:00         # Maximum runtime (D-HH:MM:SS format)
#SBATCH -p batch                # Partition (queue) to submit the job to
#SBATCH -n 1                    # Number of tasks (1 task in this case)
#SBATCH --mem=16g               # Memory allocation (32 GB)
#SBATCH --cpus-per-task=2       # CPU cores per task 
#SBATCH --output=%x-%J-%u.out
#SBATCH --error=%x-%J-%u.err
#SBATCH --mail-type=ALL
#SBATCH --mail-user=XXX@tufts.edu

# Load Nextflow (adjust module name to your system)
module load nextflow/25.04.0
module load singularity/4.3.1


# Set Singularity cache directory
# NOTE: Do not use $HOME for caching images.
# Use the system-wide cache if running nf-core pipelines managed by admins:
# export NXF_SINGULARITY_CACHEDIR=/cluster/tufts/biocontainers/nf-core/singularity-images
# Or set to your own directory if running custom pipelines.

export NXF_SINGULARITY_CACHEDIR=/cluster/tufts/biocontainers/nf-core/singularity-images

# Create output directory
mkdir -p results_test

# Run nf-core RNA-seq pipeline
nextflow run nf-core/rnaseq \
    -r 3.21.0 \
    --input samplesheet.csv \
    --outdir results_test \
    --fasta ref.fasta \
    --gtf ref.gtf \
    --aligner star_salmon \
    -profile tufts

```

### 4.2. Submitting and Monitoring

If you're running the script **directly in the terminal**, you need to make it executable first:

```
chmod +x run_nfcore_rnaseq.sh
```

However, **SLURM does not require execution permissions**, so you can submit the job as-is using:

```
sbatch run_nfcore_rnaseq.sh
```

Use the following command to check the job status:

```
squeue -u yourusername
```



### 4.3. Outputs and Next Steps

- Results: `results_test/`

- Logs: `rnaseq.<jobID>.out`, `rnaseq.<jobID>.err`, `.nextflow.log`

  

### 4.4. Additional Tips

- Test commands interactively before adding them to a job script.

- Adjust SLURM options such as `--time`, `--mem`, and `--cpus-per-task` based on dataset size and pipeline requirements.

- Review SLURM output (`.out`) and error (`.err`) files, as well as `.nextflow.log`, for troubleshooting.

- Start with small test runs before scaling up to full datasets.

  

### 4.5. Run job with GPU node

#### Interactive session

```
srun -p preempt -n 1 --time=04:00:00 --mem=20G --gres=gpu:1 --pty /bin/bash
```

You can also specify which gpu node you would like to run jobs on

```
srun -p preempt -n 1 --time=04:00:00 --mem=20G --gres=gpu:a100:1 --pty /bin/bash
```

#### Submit jobs to queue

Example script: `align.sh` using parabricks to do the alignment.

```
#!/bin/bash
#SBATCH -J fq2bam_alignment          # Job name
#SBATCH -p preempt                   # Submit to the 'preempt' partition (modify based on your cluster setup)
#SBATCH --gres=gpu:1                 # Request 1 GPU for accelerated processing
#SBATCH -n 2                         # Number of tasks (2 in this case)
#SBATCH --mem=60g                    # Memory allocation (60GB)
#SBATCH --time=02:00:00              # Maximum job run time (2 hours)
#SBATCH --cpus-per-task=20           # Number of CPU cores allocated per task
#SBATCH --output=alignment.%j.out    # Standard output file (with job ID %j)
#SBATCH --error=alignment.%j.err     # Standard error file (with job ID %j)
#SBATCH --mail-type=ALL              # Email notifications for all job states (begin, end, fail)
#SBATCH --mail-user=utln@tufts.edu   # Email address for notifications

# Load necessary modules
nvidia-smi                              # Show GPU information (optional for logging)
module load parabricks/4.0.0-1          # Load Parabricks module for GPU-accelerated alignment

# Define variables
genome_reference="/path/to/reference_genome"      # Path to the reference genome (.fasta)
input_fastq1="/path/to/input_read1.fastq"         # Path to the first paired-end FASTQ file
input_fastq2="/path/to/input_read2.fastq"         # Path to the second paired-end FASTQ file
sample_name="sample_identifier"                  # Sample identifier
known_sites_vcf="/path/to/known_sites.vcf"        # Known sites VCF file for BQSR (optional, if available)
output_directory="/path/to/output_directory"      # Directory for the output BAM file and reports
output_bam="${output_directory}/${sample_name}.bam"            # Output BAM file path
output_bqsr_report="${output_directory}/${sample_name}.BQSR-report.txt"  # Output BQSR report path

# Run the Parabricks fq2bam alignment pipeline
pbrun fq2bam \
    --ref ${genome_reference} \                # Reference genome (.fasta)
    --in-fq ${input_fastq1} ${input_fastq2} \  # Input paired-end FASTQ files
    --read-group-sm ${sample_name} \           # Sample name for read group
    --knownSites ${known_sites_vcf} \          # Known sites for BQSR
    --out-bam ${output_bam} \                  # Output BAM file
    --out-recal-file ${output_bqsr_report}     # Output Base Quality Score Recalibration (BQSR) report


```

Here is the command to submit job

```
chmod +x align.sh    # Makes the script executable
sbatch align.sh      # Submits the script to the SLURM queue
```

Use `squeue -u yourusername` to check job status.

## 5 Additional Resources

### Datasets

In bioinformatics, it’s common to download databases or reference genomes from public websites. For example, performing sequence alignment requires downloading the appropriate reference genome. To simplify this process, we have pre-downloaded and managed several databases/datasets for users. These include:

- [Alphafold2](https://rtguides.it.tufts.edu/bio/databases/alphafold.html)
- [Diamond](https://rtguides.it.tufts.edu/bio/databases/diamond.html)
- [iGenomes](https://rtguides.it.tufts.edu/bio/databases/igenomes.html)
- [Kraken2](https://rtguides.it.tufts.edu/bio/databases/kraken2.html)
- [Biobakery](https://rtguides.it.tufts.edu/bio/databases/biobakery.html)
- [geNomand](https://rtguides.it.tufts.edu/bio/databases/genomad-db.html)
- [Metaphlan](https://rtguides.it.tufts.edu/bio/databases/metaphlan.html)
- [Blast Databases](https://rtguides.it.tufts.edu/bio/databases/ncbi.html)

### New user guide

In early 2025, we launched a new [RT Guides website](https://rtguides.it.tufts.edu/index.html), offering comprehensive resources on a wide range of topics, including but not limited to HPC, data science, and and, **most importantly, [bioinformatics](https://rtguides.it.tufts.edu/bio/index.html)**. We keep up with the latest trends and regularly update our materials to reflect new developments. We highly recommend bookmarking the website and referring to it whenever you encounter challenges. Your feedback is invaluable—let us know if you spot any errors or have suggestions.

For updates on bioinformatics education, software, and tools, consider [subscribing](https://elist.tufts.edu/sympa/info/best) to our e-list: [best@elist.tufts.edu](mailto:best@elist.tufts.edu).
