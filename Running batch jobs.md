---
layout: default
---



When you connect to the HPC, you have access to (one of) the login nodes of the cluster. The computations however, should not be performed on this login node. The actual work is done on the cluster’s compute nodes. The compute nodes are managed by the job scheduling software (Moab) and a Resource Manager (TORQUE).


#### Module functions:

|                    Funcion                    |                          Explanation                         |
|:---------------------------------------------:|:------------------------------------------------------------:|
|               `module available`              |             List all currently available software            |
| ```module available \| grep -i -e "matlab"``` | Check whether some specific software is installed on the HPC |
|    `module load package1/version package2/version`                                           |     To “activate” a software package                                                         |
|    `module list`                                           |   Check modules that are currently loaded                                                           |
|     `module unload package`                                          |       To unload a module                                                       |
|       `module purge`                                        |      To unload all modules at once                                                      |
| `module help`                                              |       To get a list of all possible commands                                                       |
| `module save my-collection`                                              | Save collection of modules                                                             |
| `module restore my-collection`                                              | Load the collection of modules                                                             |
| `module savelistr`                                              | Get a list of all your saved collections                                                             |
| `module describe my-collection`                                              | To get a list of all modules a collection will load                                                             |
| `rm $HOME/.lmod.d/my-collection`                                              | To remove a collection                                                             |

#### Defining and submitting your job

Each time you want to execute a program on the HPC you’ll need 2 things:
- **The executable**: The program to execute from the end-user, together with its peripheral input.
- **A batch job script** (.pbs): It will define the computer resource requirements of the program, the required additional software packages and which will start the actual executable. The
HPC needs to know: 
	- The type of compute nodes `#PBS -N my_serial_job` 
	- The number of CPUs `#PBS -l nodes=5:ppn=2`
	- The amount of memory `#PBS -l mem=4gb`
	- The expected duration of the execution time `#PBS -l walltime=00:05:00`
	- The name of the files which will contain the output and error messages
	- What executable to start, and its arguments

|                    Funcion                    |                          Explanation                         |
|:---------------------------------------------:|:------------------------------------------------------------:|
| `qsub example.pbs`                                              |  Submit a job to the cluster’s job system for execution                                                            |
| `module swap cluster/skitty`                   | To swap to another cluster (skitty in this example)                                                             |
| `module avail cluster/`                          |  To see the available clusters                                                            |
| `qstat jobId`                                              | Keep track of a job in the cluster                                                             |

#### Running a job after another job
You can make jobs that depend on other jobs. The following example will submit 2 jobs, but the second job (job2.sh) will be held (H status in qstat) until the first job successfully completes. If the first job fails, the second will be cancelled.
```
FIRST_ID=$(qsub job1.sh)
qsub -W depend=afterok:$FIRST_ID job2.sh
```

#### Generate your own e-mail notifications

You can instruct the HPC to send an e-mail to your e-mail address whenever a job begins, ends and/or aborts, by adding the following lines to the job script fibo.pbs:

```
#PBS -m abe
```
