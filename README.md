## msync -- wrapper for rsync that allows multistream transfer of a number of large files or directory tree over high latency WAN links

msync organizes files into given number of "piles" and transfers all piles in parallel using for each separate invocation of rsync or tar pipe to the target server.

Can be used for transferring large file such as genomes files to/from AWS. Number of parallel processed launched is specified via option -p (the default is 4). 

If is recommended to split files over 5TB in chunks for transfer but currently this needs to be done manually. 

If not all files were transferred on the next invocation is calculated the differences and acts accordingly until all files or directory tree is transferred to the target server.  
For this purpose it scans the content of the remote size at the beginning and compare its status with the original : only  missing files will be transferred. 
 
With latency around 100 msec and 8 threads transfer rate varies between 50 and 100 MB/sec. Sometimes I managed to transfer over 4TB in 24 hours. 

Nikolai Bezroukov, 2018-2020. Licensed under Artistic license 

For details see http://softpanorama.org/Utilities/Msync/readme.shtml
