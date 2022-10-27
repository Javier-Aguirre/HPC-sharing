## Using SCP

### 1. From local to host
On the terminal of the local computer:
Use the `scp` command: 
`scp /local/path/file.txt vsc45436@login.hpc.ugent.be:./host/path/file.txt`
If you wish to copy and entire directory, you can make it by adding the flag `-r` as shown below:
`scp -r /local/path vsc45436@login.hpc.ugent.be:/host/path/`

### 2. From host to local

On the terminal of the local computer:
Use the `scp` command:
`scp vsc45436@login.hpc.ugent.be:./host/path/file.txt /local/path/file.txt `
If you wish to copy and entire directory, you can make it by adding the flag `-r` as shown below:
`scp -r vsc45436@login.hpc.ugent.be:/host/path/ /local/path`

## Using SFTP (Secure File Transfer Protocol)

First of all, you must start a session with the following command:
`sftp vsc45436@login.hpc.ugent.be`

Typical and popular commands inside an sftp session are:
$\begin{array}{|l|l|}
\hline \text { cd /examples/fibo } & \begin{array}{l}
\text { Move to the examples/fibo subdirectory on the HPC (i.e., the } \\
\text { remote machine) }
\end{array} \\
\hline \text { ls } & \text { Get a list of the files in the current directory on the HPC. } \\
\hline \text { get fibo.py } & \text { Copy the file "fibo.py" from the HPC } \\
\hline \text { get tutorial/HPC.pdf } & \begin{array}{l}
\text { Copy the file "HPC.pdf" from the HPC, which is in the "tutorial" } \\
\text { subdirectory. }
\end{array} \\
\hline \text { lcd test } & \text { Move to the "test" subdirectory on your local machine. } \\
\hline \text { lcd .. } & \text { Move up one level in the local directory. } \\
\hline \text { lls } & \text { Get local directory listing } \\
\hline \text { put test.py } & \text { Copy the local file test.py to the HPC. } \\
\hline \text { put test1.py test2.py } & \text { Copy the local file test1.py to the HPC and rename it to test2.py. } \\
\hline \text { bye } & \text { Quit the sftp session } \\
\hline \text { mget *.cc } & \begin{array}{l}
\text { Copy all the remote files with extension ".cc" to the local direc- } \\
\text { tory. }
\end{array} \\
\hline \text { mput *.h } & \text { Copy all the local files with extension ".h" to the HPC. } \\
\hline
\end{array}$



## Fast file transfer for large datasets
`rsync` is a fast and versatile copying tool. It can be much faster than `scp` when copying large datasets. This is an example of how to use it:
### Local to host
`rsync -rzv local/folder/ vsc45436login.hpc.ugent.be:data/`

### Host to local
`rsync -rzv vsc45436login.hpc.ugent.be:data/ local/folder/`


