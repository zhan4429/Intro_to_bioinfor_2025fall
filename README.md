## Welcome

This workshop is designed to help you get started with bioinformatics on the Tufts High-Performance Computing (HPC) cluster. We will cover:

- Working with bioinformatics tools and workflows on the command line.
- Discovering the bioinformatics resources and software available on the Tufts HPC.

## Prerequisites

You will need an [active Tufts HPC account](https://it.tufts.edu/high-performance-computing). If you are new to the HPC, we strongly recommend reviewing our recent [Intro to HPC workshop](https://tufts.zoom.us/rec/play/O1Zm1daWzJdvy2yciGGUwTZCSa1cUyu4wr89gk52-EYE99jr2iWnqgok3RC6QRMPGAvnH85pRvGgVfd8.SJyARyf_p10iqYqH).

<div style="padding: 15px; margin-bottom: 20px; border: 1px solid #c3e6cb; border-radius: 6px; color: #155724; background-color: #d4edda;">
    <strong>TIP:</strong> To test your account, try logging in to <a href="https://ondemand.pax.tufts.edu">Tufts OnDemand</a>. If you can log in successfully, you’re all set. If not, please reach out to <strong>tts-research@tufts.edu</strong> for assistance.
</div>

## Connecting to the Cluster & Starting a Job

You can connect to the cluster using a terminal application (like Terminal on macOS or MobaXterm on Windows) or through the web-based Open OnDemand portal.

### Using the Command Line (SSH)

To connect, use the `ssh` command with your Tufts UTLN.

- **New Cluster:**
  ```bash
  ssh your_utln@login-prod.pax.tufts.edu
  ```
- **Old Cluster:**
  ```bash
  ssh your_utln@login.pax.tufts.edu
  ```

<div style="padding: 15px; margin-bottom: 20px; border: 1px solid #ffeeba; border-radius: 6px; color: #856404; background-color: #fff3cd;">
<strong>WARNING:</strong> <strong>Do not run jobs on login nodes.</strong> Login nodes are shared resources with limited CPU and memory. They should only be used for light tasks like submitting jobs, managing files, and editing scripts.
</div>

To start an interactive session on a compute node, use the `srun` command:

```bash
srun -N1 -n2 -t2:00:00 --pty bash
```

This command requests an interactive session with the following resources:

- `-N1`: 1 node
- `-n2`: 2 CPU cores
- `-t2:00:00`: A time limit of 2 hours

<img src="https://it.fysik.su.se/hpc/_images/slurm.png" alt="SLURM cluster architecture diagram">

### Using Open OnDemand

You can also access the cluster through a web browser via Open OnDemand.

- **New Open OnDemand:** [https://ondemand-prod.pax.tufts.edu](https://ondemand-prod.pax.tufts.edu)
- **Old Open OnDemand:** [https://ondemand-pax.pax.tufts.edu](https://ondemand-pax.pax.tufts.edu)

## Agenda

- [Introduction to the Linux/Unix Command Line](tutorials/01-linux.md)
- [Bioinformatics on the Tufts HPC](tutorials/02-bioinfo.md)

<div style="padding: 15px; margin-bottom: 20px; border: 1px solid #bee5eb; border-radius: 6px; color: #0c5460; background-color: #d1ecf1;">
<strong>NOTE:</strong> Access to the new cluster and new Open OnDemand is not enabled by default. To apply for access, you must join the <a href="https://tufts.qualtrics.com/jfe/form/SV_08IS0n1YSTR6KRU">HPC Upgrade Early Adopter Program</a>.
</div>

## Recording

<div style="padding: 15px; margin-bottom: 20px; border: 1px solid #bee5eb; border-radius: 6px; color: #0c5460; background-color: #d1ecf1;">
<strong>NOTE:</strong> A recording of this workshop will be made available after the session.
</div>

## Upcoming Research Technology Workshops

- **Introduction to Programming with Python**
  - _October 9, 2025, 3:00pm - 5:00pm_
- **Introduction to Git & GitHub**
  - _October 15, 2025, 1:00pm - 3:00pm_
- **Introduction to Research Computing Tiered Storage**
  - _Tuesday, October 21, 2025, 11:00am - 12:00pm_
- **Using the newly upgraded HPC Cluster**
  - _Thursday, October 23, 2025, 1:00pm - 3:00pm_
- **Best Practices for using GPUs in Jupyter for Data Science**
  - _Wednesday, October 29, 2025, 2:00pm - 3:30pm_

For a full list, please visit: [https://go.tufts.edu/workshops](https://go.tufts.edu/workshops)
