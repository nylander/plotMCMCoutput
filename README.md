# plotMCMCoutput

## Description

Shell scripts (bash) for plotting MCMC output from, e.g.,
[MrBayes](https://github.com/NBISweden/MrBayes/), [BEAST
X](https://beast.community/), [BEAST 2](https://www.beast2.org/) etc, using
[gnuplot](http://www.gnuplot.info).

## Installation and dependencies

The scripts are written in Bash (tested on bash v5.2.21), and uses the software
[gnuplot](http://www.gnuplot.info/) for plotting. On a Debian-based system
using `apt` (e.g. \*buntu), `gnuplot` can be installed with `sudo apt install
gnuplot`.

The files in the folder [apptainer](apptainer/README.md) describes how to
install gnuplot and scripts as a container.

## Usage (main script `plotMCMCoutput.sh`)

    $ plotMCMCoutput.sh [options] file(s)

## Options (main script `plotMCMCoutput.sh`)

    -b burnin      specify the number of generations to be discarded
    -c column      specify column number (first column is nr. 1) to plot
    -h             print help message
    -i             get info on column names (if applicable)
    -l             plot a growing ("live") file to file or terminal
    -o file.png    plot to file (png format)
    -t             plot in terminal instead of file
    -v             be verbose
    -x column      use together with -y to plot column y against column x
    -y column      as -c, or use with -x to plot column y against column x

## Examples

#### Plot trace of log Likelihood in MrBayes .p files

    $ plotMCMCoutput.sh data/*.p

![Plot lnL](img/lnL.png)

#### Plot trace of log Likelihood with burnin = 50

    $ plotMCMCoutput.sh -b 50 data/*.p

![Plot lnL with burnin](img/lnL-burn.png)

#### Plot trace of log Likelihood in terminal (no graphics)

    $ plotMCMCoutput.sh -t data/*.p

![Plot lnL in terminal](img/lnL-term.png)

#### Plot trace of log Likelihood to file (PNG)

    $ plotMCMCoutput.sh -o out.png data/*.p

#### Plot trace of log Likelihood from a growing ("live") file

    $ plotMCMCoutput.sh -l data/*.p

![Plot lnL live](img/live.gif)

    $ plotMCMCoutput.sh -t -l data/*.p

![Plot lnL live in terminal](img/live-term.gif)

#### Find out what parameters you have in the p file

    $ plotMCMCoutput.sh -i data/run1.p
       1	Gen
       2	LnL
       3	TL
       4	pi(A)
       5	pi(C)
       6	pi(G)
       7	pi(T)

#### Plot selected columns

    $ plotMCMCoutput.sh -c 3 data/*.p

![Plot column 3](img/col-3.png?raw=true "Plot column 3")

    $ plotMCMCoutput.sh -t -c 3 data/*.p

![Plot column 3 in terminal](img/col-3-term.png)

    $ plotMCMCoutput.sh -x 4 -y 7 data/*.p

![Plot columns 4 against 7](img/col-4-7.png)

    $ plotMCMCoutput.sh -t -x 4 -y 7 data/*.p

![Plot columns 4 against 7 in terminal](img/col-4-7-term.png)

### Plot average standard deviation of split frequencies, specifying 0.03 as the treshold

    $ plotstddev data/runs.1.2.mcmc 0.03

![Plot AvgStdDev](img/stddev.png)

    $ plotstddev_term.sh -t data/runs.1.2.mcmc 0.03

![Plot AvgStdDev in terminal](img/stddev-term.png)

## Files

- [`plotMCMCoutput.sh`](plotMCMCoutput.sh) -- General script for quickly
  plotting column data.
- [`plotstddev`](plotstddev) -- Plot the standard deviation of split
  frequencies in a MrBayes .mcmc file.
- [`plotstddev_term.sh`](plotstddev_term.sh) -- Plot the standard deviation of
  split frequencies in a MrBayes .mcmc file, but plot in terminal window
  instead of device.
- [data/run1.p](data/run1.p) -- Example parameter file from MrBayes v.3
- [data/run2.p](data/run2.p) -- Example parameter file from MrBayes v.3
- [data/runs.1.2.mcmc](data/runs.1.2.mcmc) -- Example .mcmc file from MrBayes
  v.3
- [apptainer/](apptainer/README.md) -- Files for running plotMCMCoutput.sh as a
  singularity/apptainer image

## License and Copyright

Copyright (c) 2010-2025 Johan Nylander. MIT [LICENSE](LICENSE)

## Download

<https://github.com/nylander/plotMCMCoutput>
