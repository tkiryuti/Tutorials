# Parallelization in PACE

## Options
* [Job Arrays](#job-arrays)
* [GNU Parallel](#gnu-parallel)
* [Launcher](#launcher)
* [pylauncher](#pylauncher)

## When to use each type of Parallelization

### [Job Arrays](http://docs.pace.gatech.edu/software/arrayGuide/)

### [GNU Parallel](http://docs.pace.gatech.edu/software/multiparallel/)

### [Launcher](http://docs.pace.gatech.edu/software/launcher/)

To see PACE's example of using launcher, run the command below. 
It will create a directory with an example PBS batch file and a README file with more details.
```bash
pace-getexample launcher
```

#### Important things to note about Launcher:
* It is preferred by PACE over using Job Arrays.
* It only supports single-core jobs.
* It assumes that we are using the same number of cores on each node.


### [pylauncher](http://docs.pace.gatech.edu/software/pylauncher/)

Pylauncher uses all features of [Launcher](#launcher) but with additions. You start a small python script to mimic the behavior of Launcher.

