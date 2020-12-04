```markdown

# PFAM analysis

This tutorial will take you through the basic steps of identifying and analyzing PFAM domains in proteins. 

1. Have the FASTA file with sequences of interest ready.

2. Download the script pfam_scan.pl from http://ftp.ebi.ac.uk/pub/databases/Pfam/Tools/

3. Download the PFAM HMMs

Download the latest release from http://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/

	wget http://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.hmm.gz
	wget http://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.hmm.dat.gz
	wget http://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/active_site.dat.gz

4. Create the binary files for PFAM-A.hmm, like so
	module load hmmer
	hmmpress Pfam-A.hmm



5. Run this job script:
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
#!/bin/bash

# Copy/paste this job script into a text file and submit with the command:
#    sbatch thefilename

#SBATCH --time=12:00:00   # walltime limit (HH:MM:SS)
#SBATCH --nodes=1   # number of nodes
#SBATCH --ntasks-per-node=16   # 16 processor core(s) per node 
#SBATCH --job-name="pfam"
#SBATCH --mail-user=vrmuthye@iastate.edu   # email address
#SBATCH --mail-type=BEGIN
#SBATCH --mail-type=END
#SBATCH --mail-type=FAIL

# LOAD MODULES, INSERT CODE, AND RUN YOUR PROGRAMS HERE

module purge
module unuse /opt/rit/spack-modules/lmod/linux-rhel7-x86_64/Core
module use /opt/rit/modules
module load pfamscan

pfam_scan.pl -fasta allmuts.fasta -dir /work/LAS/dlavrov-lab/muts/domain_search -outfile allmuts.pfam -clan_overlap -e_seq 0.00001

>>>>>>>>>>>>>>>>>>>>>>>>
```

