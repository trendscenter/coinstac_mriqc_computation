#coinstac_mriqc_computation
This computation run mriqc tool(developed by poldracklab) on smri, fmri bids datasets to create quality control visual reports, which helps to identify outlier subjects in the data. 

The computation runs serially and each scan takes approximately 10 mins to run on a system with 2.3 GHz,i5 equivalent processor and 8GB RAM. Each scan output directory takes about 15MB space after running this computation. 

IMPORTANT REQUIREMENT to run this code:
if you are running >=10 subjects , we recommend that atleast 5GB of RAM should be dedicated for this docker, otherwise memory error can occur: 
"Standard error: Image Exception : #99 :: Out of memory
Cannot allocate memory"

Additionally, you can implement the following as needed:
You can reduce the number of subjects processed in parallel using the option --n_procs. Please make sure that the option --ants-nthreads is less or equal to --n_procs, except for --n_procs == 1 in which case you can use your 8 cpus (--ants-nthreads 8) for registration. You can pin the execution to a limited amount of subjects with the argument --participant_label 001 002.
Please make sure to have the space and resources to run this computation. --mem_gb 5 option here sets the max. memory to 5GB.

Example run below:

On the host machine after the docker service is started , the foll. commands are run from the terminal:

docker run -it --rm -v inputBidsDir:/data:ro -v tempWriteDir:/out poldracklab/mriqc:latest /data /out participant -m bold --verbose-reports --mem_gb 5

docker run -it --rm -v inputBidsDir:/data:ro -v tempWriteDir:/out poldracklab/mriqc:latest /data /out participant -m group --verbose-reports --mem_gb 5

After the computation finishes , the docker will exit.
