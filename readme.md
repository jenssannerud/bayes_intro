# Bayes Intro

This repository introduces bayesian phylogenetics with [revbayes](http://revbayes.github.io/). It is based on the excellent [lab](https://molevol.mbl.edu/index.php/RevBayes) at the [Workshop on Molecular Evolution](https://molevol.mbl.edu/index.php/Main_Page) by Tracy Heath and Michael Landis.

## Installing RevBayes

### Mac

If you don't already have one, create a `~/bin` folder:

    cd ~
    ls
    mkdir bin

Download the mac version of RevBayes from [here](http://revbayes.github.io/code.html), and then copy the `rb` file to the `bin` file you created above.

Next, create a `~/lib` folder if you don't already have one:

    cd ~
    ls
    mkdir bin

And copy the `boost_1_55_0` folder from the RevBayes download to this `~/lib` folder.

Add the following lines to `~/.bash_profile` (create this file if it doesn't already exist):

    export PATH=$PATH:~/bin
    export DYLD_LIBRARY_PATH=~/lib/boost_1_55_0/stage/lib


### Linux

You will need to compile from the [source](https://github.com/revbayes/revbayes).

## Jukes Cantor analysis

Fork and clone this repository. `cd` to the repository directory on your computer.

First examine the relationships of the primates under the JC model. See `RB_CTMC_Tutorial_unconstrained.pdf` for a step-by step description of the analyses. You will use revbayes to run the `JukesCantor.Rev` script, which analyzes the data in `data/primates_cytb.nex`. In the repository folder, run the following to launch the analyses:

    rb JukesCantor.Rev

The output will be in a new `output` folder. Inspect the `.log` files with Tracer, and the `.tree` file with FigTree.

Compare the parameter estimates and trees from the two different runs.

## Jukes Cantor analysis, no burnin

    rb JukesCantorNoBurn.Rev

## GTR analysis

As above, but run:

	rb GTR_Gamma.Rev

Compare the parameter estimates and trees from the two different runs.

## Running on empty

In the above analyses, the priors were set in the script and the data informed the posteriors. By not clampting the data, we can "run the analysis on empty", ie not inform the posterior by the data. This is an opportunity to explore the results based on priors only. Run:

    rb GTR_GammaEmpty.Rev

In Tracer, open the `.log` files from this run and the GTR run above. Compare the parameter estimates.

Open the trees in FigTree. How do the resuls differ from the GTR run above, where we clamped the data?


