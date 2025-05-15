# plotMCMCoutput.sh in a Apptainer/Singularity container

## Description

Script and [apptainer](https://apptainer.org/) definition file for running
plotMCMCoutput.sh in a container.

1. Get definifion file
<https://github.com/nylander/plotMCMCoutput/apptainer/plotMCMCoutput.def>

2. Build locally

        $ sudo apptainer build plotMCMCoutput.sif plotMCMCoutput.def

3. Run

        $ ./plotMCMCoutput.sif -h

## Specifics for running plotMCMCoutput.sh on [Dardel](https://www.pdc.kth.se/hpc-services/computing-systems/dardel-hpc-system)

Build on local computer as above, then copy both script
([plotMCMCoutput](plotMCMCoutput))
and image file to Dardel:

    $ scp plotMCMCoutput.sif dardel.pdc.kth.se:~/bin
    $ scp plotMCMCoutput dardel.pdc.kth.se:~/bin

Run on dardel:

    $ chmod +x ~/bin/plotMCMCoutput*
    $ plotMCMCoutput -h

    # Alt.
    $ module load PDC apptainer
    $ plotMCMCoutput.sif -h
