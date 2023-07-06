# plotMCMCoutput

Shell scripts (bash) for plotting MCMC output (e.g., from [MrBayes](http://mrbayes.sourceforge.net/) v.3, [BEAST](http://beast.bio.ed.ac.uk/), etc) using [gnuplot](http://www.gnuplot.info).

## Usage

    $ plotMCMCoutput.sh [-b burnin] [-o file | -l, -t] [[-c column] | [-x column][-y column]] file(s)

### Examples

1. Plot trace of log Likelihood in MrBayes .p files

        $ plotMCMCoutput.sh *.p

![gnuplot output](img/lnL.png?raw=true "Plot lnL")

2. Plot trace of log Likelihood with burnin = 50

        $ plotMCMCoutput.sh -b 50 *.p

![gnuplot output](img/lnL-burn.png?raw=true "Plot lnL with burnin")

3. Plot trace of log Likelihood in terminal (no graphics)

        $ plotMCMCoutput.sh -t *.p

![gnuplot output](img/lnL-term.png?raw=true "Plot lnL in terminal")

4. Plot trace of log Likelihood to file (PNG)

        $ plotMCMCoutput.sh -o out.png *.p

5. Plot trace of log Likelihood from a growing ("live") file

        $ plotMCMCoutput.sh -l *.p

![gnuplot output](img/live.gif?raw=true "Plot lnL live")

        $ plotMCMCoutput.sh -t -l *.p

![gnuplot output](img/live-term.gif?raw=true "Plot lnL live in terminal")

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

![gnuplot output](img/col-3.png?raw=true "Plot column 3")

        $ plotMCMCoutput.sh -t -c 3 *.p

![gnuplot output](img/col-3-term.png?raw=true "Plot column 3 in terminal")

        $ plotMCMCoutput.sh -x 4 -y 7 *.p

![gnuplot output](img/col-4-7.png?raw=true "Plot columns 4 against 7")

        $ plotMCMCoutput.sh -t -x 4 -y 7 *.p

![gnuplot output](img/col-4-7-term.png?raw=true "Plot columns 4 against 7 in terminal")

8. Plot average standard deviation of split frequencies, specifying 0.03 as the treshold

        $ plotstddev runs.1.2.mcmc 0.03

![gnuplot output](img/stddev.png?raw=true "Plot AvgStdDev")

        $ plotstddev_term.sh -t runs.1.2.mcmc 0.03

![gnuplot output](img/stddev-term.png?raw=true "Plot AvgStdDev in terminal")

## Files

* [plotMCMCoutput.sh](https://github.com/nylander/plotMCMCoutput/blob/master/plotMCMCoutput.sh) -- General script for quickly plotting column data.

* [plotstddev](https://github.com/nylander/plotMCMCoutput/blob/master/plotstddev) -- Plot the standard deviation of split frequencies in a MrBayes .mcmc file.

* [plotstddev_term.sh](https://github.com/nylander/plotMCMCoutput/blob/master/plotstddev_term.sh) -- Plot the standard deviation of split frequencies in a MrBayes .mcmc file, but plot in terminal window instead of device.

* [run1.p](https://github.com/nylander/plotMCMCoutput/blob/master/run1.p) -- Example parameter file from MrBayes v.3

* [run2.p](https://github.com/nylander/plotMCMCoutput/blob/master/run2.p) -- Example parameter file from MrBayes v.3

* [runs.1.2.mcmc](https://github.com/nylander/plotMCMCoutput/blob/master/runs.1.2.mcmc) -- Example .mcmc file from MrBayes v.3


## Dependencies

All scripts are dependent on the [gnuplot](http://www.gnuplot.info/) software.

## Licence and Copyright

Copyright (c) 2010-2023 Johan Nylander

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
