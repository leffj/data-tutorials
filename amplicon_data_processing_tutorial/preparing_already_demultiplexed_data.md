# Preparing already demultiplexed data for UPARSE

This typically applies when the sequence library prep uses standard Illumina barcodes that are ligated onto the amplicons of interest. In this case, these barcodes and corresponding sample IDs are input to the Illumina software when sequencing is performed, and the sequencer outputs separate files for each sample, already demultiplexed.

However, for our purposes, we want sequences from all samples to be contained in the same file and the headers for each sequence to identify which sample a given sequence came from. To do, this create a mapping file that links sample IDs to sequence file paths. Your mapping file should look similar to this:

| #SampleID | Forward_filepath | Reverse_filepath |
|-----------|------------------|------------------|
| 107.I     | /data/shared/2014_02_03_data_tutorial/separate_files_per_sample/107.I_1.fq | /data/shared/2014_02_03_data_tutorial/separate_files_per_sample/107.I_2.fq|
| 992.O     | /data/shared/2014_02_03_data_tutorial/separate_files_per_sample/992.O_1.fq | /data/shared/2014_02_03_data_tutorial/separate_files_per_sample/992.O_2.fq|

To do the formatting, run this command using your own mapping file. This example assumes the mapping file name is: `Demo_16S_MappingFile_sep_files.txt`

  format_multifile_headers_uparse.py -i Demo_16S_MappingFile_sep_files.txt -o demultiplexed_seqs

Now you can use the sequences as normal in the rest of the pipeline.
