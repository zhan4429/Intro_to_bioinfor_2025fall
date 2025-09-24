# Getting Started with Bioinformatics on Tufts HPC

## Welcome

This workshop is designed to help you:

- Begin working with bioinformatics tools and workflows—especially those that use the command line—on the Tufts HPC.
- Get familiar with the bioinformatics resources and software available on the Tufts HPC.

## Prerequisites

You will need an [active Tufts HPC account](https://it.tufts.edu/high-performance-computing).

If you’re new to HPC, please review our recent [Intro to HPC](https://tufts.zoom.us/rec/play/O1Zm1daWzJdvy2yciGGUwTZCSa1cUyu4wr89gk52-EYE99jr2iWnqgok3RC6QRMPGAvnH85pRvGgVfd8.SJyARyf_p10iqYqH?eagerLoadZvaPages=sidemenu.billing.plan_management&accessLevel=meeting&canPlayFromShare=true&from=share_recording_detail&startTime=1758646989000&componentName=rec-play&originRequestUrl=https%3A%2F%2Ftufts.zoom.us%2Frec%2Fshare%2FwmG-yY1txV5PNtlN4Wp6n8cM6fyXcPNx5uly4gi61V3tIH0RJ6Plqsxrz2fK4AzQ.7q1T6Xpaxe4kfKnd%3FstartTime%3D1758646989000) workshop.

> **Tip:** To test your account, log in to [Tufts OnDemand](https://ondemand.pax.tufts.edu).
>
> - If you can log in successfully, you’re all set.
> - If not, please reach out to **tts-research@tufts.edu** for assistance.

## Login the cluster and start an interactive job

### Using terminal app

```
## For old cluster
ssh your_utln@login.pax.tufts.edu
## For new cluster
ssh your_utln@login-prod.pax.tufts.edu
## Start an interactive job
srun -N1 -n2 -t2:00:00 --pty bash ## You will start an interactive session with 1 node and 2 cores for 2 hours
```

### Open OnDemand

- Old Open OnDemand: [https://ondemand-pax.pax.tufts.edu](https://ondemand.pax.tufts.edu)
- New Open OnDemand: [https://ondemand-prod.pax.tufts.edu](https://ondemand-prod.pax.tufts.edu)

## Agenda

- [Introduction to the Linux/Unix Command Line](tutorials/01-linux.md)
- [Bioinformatics on the Tufts HPC](tutorials/02-bioinfo.md)

<div style="border-left: 4px solid #007acc; padding: 0.5em 1em; background: #f0f8ff;">
<strong>Note:</strong> Users do not have access to the new cluster and new Open OnDemand by default.  
To apply for access, you need to join the <a href="https://tufts.qualtrics.com/jfe/form/SV_08IS0n1YSTR6KRU" target="_blank">HPC Upgrade Early Adopter Program</a>.
</div>

## Recording

A recording of this workshop will be made available after the session.

## Upcoming research technology workshops

- Introduction to Programming with Python, October 9, 2025, 3:00pm - 5:00pm

- Introduction to Git & GitHub , October 15, 2025, 1:00pm - 3:00pm

- Introduction to Research Computing Tiered Storage Tuesday, October 21, 2025 11:00am - 12:00pm

- Using the newly upgraded HPC Cluster Thursday, October 23, 2025 1:00pm - 3:00pm

- Best Practices for using GPUs in Jupyter for Data Science Wednesday, October 29, 2025 2:00pm - 3:30pm

More Research Technology Workshops: [https://go.tufts.edu/workshops](https://go.tufts.edu/workshops******)
