# BWAF

# Commands **To download the human genome DNA sequence (FASTA format, GRCh38 primary assembly)**
1.  **To download the human genome DNA sequence (FASTA format, GRCh38 primary assembly):**
    ```bash
    wget ftp://ftp.ensembl.org/pub/release-110/fasta/homo_sapiens/dna/Homo_sapiens.GRCh38.dna.primary_assembly.fa.gz
    ```

2.  **To download the human gene annotation (GTF format, GRCh38 release 110):**
    ```bash
    wget ftp://ftp.ensembl.org/pub/release-110/gtf/homo_sapiens/Homo_sapiens.GRCh38.110.gtf.gz
    ```

**Explanation of the commands:**

*   `wget`: A command-line utility for downloading files from the web.
*   `ftp://ftp.ensembl.org/...`: The FTP URL pointing to the specific files on the Ensembl server.
    *   `pub/release-110/`: Indicates these files are from Ensembl release 110.
    *   `fasta/homo_sapiens/dna/`: Path for DNA sequences in FASTA format for Homo sapiens.
    *   `gtf/homo_sapiens/`: Path for gene annotations in GTF format for Homo sapiens.
    *   `Homo_sapiens.GRCh38.dna.primary_assembly.fa.gz`: The actual FASTA file for the primary genome assembly.
    *   `Homo_sapiens.GRCh38.110.gtf.gz`: The actual GTF annotation file for release 110 of the GRCh38 assembly.
*   `.gz`: Indicates that the files are compressed using gzip. You would typically decompress them using `gunzip <filename.gz>` after downloading.
