# coinstac_mriqc_computation
This computation run mriqc tool(developed by poldracklab) on smri, fmri bids datasets to create quality control visual reports, which helps to identify outlier subjects in the data. 

The computation runs serially and each scan takes approximately 10 mins to run on a system with 2.3 GHz,i5 equivalent processor and 8GB RAM. Each scan output directory takes about 15MB space after running this computation. 

*IMPORTANT REQUIREMENT to run this code:
Atleast 5GB of RAM should be dedicated for this docker. Please make sure to have the space and resources to run this computation. 

Example run below:

docker run -it --rm -v /Users/Downloads/ds003/:/data:ro -v /Users/Downloads/bids_mriqc:/out poldracklab/mriqc:latest /data /out participant -m bold --verbose-reports

docker run -it --rm -v /Users/spanta/Downloads/ds003/:/data:ro -v /Users/spanta/Downloads/bids_mriqc:/out poldracklab/mriqc:latest /data /out participant -m group --verbose-reports

After the computation finishes , the docker will exit.
