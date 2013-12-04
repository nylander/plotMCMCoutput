plotMCMCoutput
==============

Shell scripts (bash) for plotting MCMC output (e.g., from MrBayes v.3, BEAST, etc) using gnuplot


Usage
-----

    plotMCMCoutput.sh *.p


Files
-----

* plotMCMCoutput.sh       -- General script for quickly plotting column data.

                             For example, to plot several MrBayes *.p files overlayed (use 'plotMCMCoutput.sh -h' for more info on options):

                                 plotMCMCoutput.sh *.p



* plotstddev              -- Plot the standard deviation of split frequencies in a MrBayes .mcmc file
                             For example:

                                 plotstddev runs.1.2.mcmc 0.03

* plotstddev_term.sh      -- Plot the standard deviation of split frequencies in a MrBayes .mcmc file,
                             but plot in terminal window instead of device.


* run1.p                  -- Example parameter file from MrBayes v.3

* run2.p                  -- Example parameter file from MrBayes v.3

* runs.1.2.mcmc           -- Example .mcmc file from MrBayes v.3


* plotMCMCoutput.png      -- Example output on device

* plotMCMCoutput_term.png -- Example output in terminal

* plotstddev.png          -- Example output on device

* plotstddev_term.png     -- Example output in terminal 


Dependencies
------------

All scripts are dependent on the presence of [gnuplot](http://www.gnuplot.info/)


