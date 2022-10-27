### Pre-defined user directories

- Long-term storage slow filesystem, intended for smaller files: 

	| Variable | Description |
	|:--------:|:------------:|
	| $VSC_HOME | For your configuration files and other small files. The default directory is `/user/gent/xxx/vsc45436`| 
	| $VSC_DATA | A bigger “workspace”, for datasets, results, logfiles. The default directory is `/data/gent/xxx/vsc45436` |
	
- Fast temporary storage:

	| Variable | Description |
	|:--------:|:------------:|
	| $VSC_SCRATCH_NODE | For temporary or transient data on the local compute node, where fast access is important. The default directory is `/tmp`. |
	| $VSC_SCRATCH | For temporary or transient data that has to be accessible from all nodes of a cluster (including the login nodes). The default directory is `/scratch/gent/xxx/vsc45436` |
	| $VSC_SCRATCH_SITE | Currently the same as $VSC_SCRATCH, but could be used for a scratch space shared across all clusters at a site in the future. |
	| $VSC_SCRATCH_GLOBAL | Currently the same as $VSC_SCRATCH, but could be used for a scratch space shared across all clusters of the VSC in the future. |
	| $VSC_SCRATCH_CLUSTER | The scratch filesystem closest to this cluster. |
	| $VSC_SCRATCH_ARCANINE | A separate (smaller) shared scratch filesystem, powered by SSDs. This scratch filesystem is intended for very I/O-intensive workloads. |



