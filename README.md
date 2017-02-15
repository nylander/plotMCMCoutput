# plotMCMCoutput

Shell scripts (bash) for plotting MCMC output (e.g., from [MrBayes](http://mrbayes.sourceforge.net/) v.3, [BEAST](http://beast.bio.ed.ac.uk/), etc) using [gnuplot](http://www.gnuplot.info).

![gnuplot output](img/lnL.png?raw=true "Plot lnL")
![gnuplot output](img/lnL-term.png?raw=true "Plot lnL term")

![gnuplot output](img/xy.png?raw=true "Plot lnL")
![gnuplot output](img/xy-term.png?raw=true "Plot lnL term")

![gnuplot output](img/stddev.png?raw=true "Plot stddev")
![gnuplot output](img/stddev-term.png?raw=true "Plot stddev term")


## Usage

    $ plotMCMCoutput.sh -h

### Examples

1. Plot trace of log Likelihood

        $ plotMCMCoutput.sh *.p

2. Plot trace of log Likelihood with burnin = 50

        $ plotMCMCoutput.sh -b 50 *.p

3. Plot trace of log Likelihood in terminal (no graphics)

        $ plotMCMCoutput.sh -t *.p

4. Plot trace of log Likelihood to file (PNG)

        $ plotMCMCoutput.sh -o out.png *.p

5. Plot trace of log Likelihood in terminal from a growing ("live") file

        $ plotMCMCoutput.sh -t -l *.p

6. Find out what parameters you have in the p file:

        $ grep '^Gen' run1.p | tr '\t' '\n' | nl
            1	Gen
            2	LnL
            3	TL
            4	pi(A)
            5	pi(C)
            6	pi(G)
            7	pi(T)

7. Plot selected columns

        $ plotMCMCoutput.sh -c 3 *.p
        $ plotMCMCoutput.sh -x 4 -y 7 *.p


## Files

* [plotMCMCoutput.sh](https://github.com/nylander/plotMCMCoutput/blob/master/plotMCMCoutput.sh) -- General script for quickly plotting column data. For example, to plot several MrBayes \*.p files overlayed (use `plotMCMCoutput.sh -h` for more info on options):

        $ plotMCMCoutput.sh *.p

* [plotstddev](https://github.com/nylander/plotMCMCoutput/blob/master/plotstddev) -- Plot the standard deviation of split frequencies in a MrBayes .mcmc file. For example:

        $ plotstddev runs.1.2.mcmc 0.03

* [plotstddev_term.sh](https://github.com/nylander/plotMCMCoutput/blob/master/plotstddev_term.sh) -- Plot the standard deviation of split frequencies in a MrBayes .mcmc file, but plot in terminal window instead of device.

* [run1.p](https://github.com/nylander/plotMCMCoutput/blob/master/run1.p) -- Example parameter file from MrBayes v.3

* [run2.p](https://github.com/nylander/plotMCMCoutput/blob/master/run2.p) -- Example parameter file from MrBayes v.3

* [runs.1.2.mcmc](https://github.com/nylander/plotMCMCoutput/blob/master/runs.1.2.mcmc) -- Example .mcmc file from MrBayes v.3


## Dependencies

All scripts are dependent on the [gnuplot](http://www.gnuplot.info/) software.


