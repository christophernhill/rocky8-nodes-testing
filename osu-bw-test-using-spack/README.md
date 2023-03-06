# Spack based Slurm script to install and run compiler, MPI and OSU Micro Benchmarks

The contents of this directory are as follows

1. `test.slurm.sh`
   
     * Script that can be run through Slurm requesting two nodes. 
     * The script has one configurable parameter `WDIR`. This must be set to a working directory for building and running software. 
     * When the script is run it will install needed software to run the OSU micro benchmarks that measure MPI meesage bandwidth and latency between two nodes.
     * After editing `WDIR` to a valid directory, visible on all nodes the script can be run using the command
     
       `$ sbatch < test.slurm.sh`
     
     * The script executes the following steps
        
          - creates a working directory 
          - downloads spack
          - set spack environment variables
          - downloads, builds and installs a recent gcc (12.2.0)
          - rebuilds gcc 12.2.0 with CPU target zen3
          - downloads, builds and installs a recent version of the MVAPICH distribution of MPI ( mvapich 2.3.7 )
          - downloads, builds and installs the latest spack version of the OSU MPI micro benchmarks
          - generates and LMOD Modules directory for the built software
          - loads modules for mvapich and the OSU MPI micro benchmarks
          - runs the OSU benchmarks `osu_bw`, `osu_latency`, `osu_bibw` between two nodes


2. `sample-output-for-build-from-clean.txt`

3. `sample`
