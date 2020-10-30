## msync -- wrapper for rsync that allows multistream transfer of a number of large compressed archives or a directory tree with them over high latency WAN links

msync organizes files into given number of "piles" and transfers all piles in parallel using for each separate invocation of rsync or tar pipe to the target server.

Designed for transferring large compressed arhives, such as compressed tarball of genomes trees to/from AWS. It does not compress the stream and as such is not well suited for trasmission of uncompressed text files like FASTA files.  

The number of parallel processed launched is specified via option -p (the default is 4). 

If is recommended to split files over 5TB in chunks for transfer, but currently this needs to be done manually. 

If not all files were transferred on the next invocation the utility  calculates the differences and acts accordingly until all files in the list or a directory tree are transferred to the target server.  Text fiels which can have differences due to the differences in encoding are ignored in partical transferes. 

IF the untlity did not manage to transfere all files onthe first run, onthe next run  t scans the content of the remote size at the beginning and compares its status with the original : only missing and incomplete archives will be transferred. 
 
With latency around 100 msec and 8 threads transfer rate varies between 50 and 100 MB/sec. Sometimes I managed to transfer over 4TB in 24 hours. 

Nikolai Bezroukov, 2018-2020. Licensed under Artistic license 

For details see http://softpanorama.org/Utilities/Msync/readme.shtml
