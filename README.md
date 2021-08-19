# uwb_hyak_resources
Resources for users of the UWB Hyak nodes

Official Hyak documentation:
https://hyak.uw.edu/docs

Cheat sheet:

Login:  
ssh [netid]@klone.hyak.uw.edu
  
copy file to server from local directory:  
scp [source filepath] [destination directory]  
scp /mnt/c/Users/Dylan/Documents/zaneveld/klone/gcmp/procedure/denoise.py /gscratch/zaneveld/sonettd/gcmp/procedure

view available resources:  
hyakalloc

request compute node (activate screen (https://linuxize.com/post/how-to-use-linux-screen/) first; it doesn't seem like it can be activated from a compute node):  
srun -A zaneveld -p compute-bigmem --time=[hours:minutes:seconds] --mem=[memory amount]G --pty /bin/bash

view active compute nodes:  
squeue -A zaneveld

rejoin compute node already allocated:  
sattach [jobid].0



From experience - it's a good idea to use os.path.exists() to ensure that the directory to which you want to save your results actually exists, *before* running the actual computation in your script. That way you don't waste *mumble* hundred hours running a command only for the script to fail to save the result when you forgot to add an output directory.
