# Parallelization in PACE

## Options
* [Job Arrays](#job-arrays)
* [GNU Parallel](#gnu-parallel)
* [Launcher](#launcher)
* [pylauncher](#pylauncher)

## When to use each type of Parallelization

## [Job Arrays](http://docs.pace.gatech.edu/software/arrayGuide/)

## [GNU Parallel](http://docs.pace.gatech.edu/software/multiparallel/)

To see PACE's example of using GNU Parallel, run the command below. 
It will create a directory with an example PBS batch file and a README file with more details.
```bash
pace-getexample gnu_parallel
```

### Important things to note about GNU Parallel:
* [Tutorial from the GNU Parallel website](https://www.gnu.org/software/parallel/parallel_tutorial.html)
* 

## [Launcher](http://docs.pace.gatech.edu/software/launcher/)

To see PACE's example of using Launcher, run the command below. 
It will create a directory with an example PBS batch file and a README file with more details.
```bash
pace-getexample launcher
```

### Important things to note about Launcher:
* It is preferred by PACE over using [Job Arrays](#job-arrays).
* It only supports single-core jobs.
* It assumes that we are using the same number of cores on each node.
* Jobs can run in any order so there must not be dependencies between jobs.

### Summary of Launcher usage:
#### 1. Set 3 different environment variables.
* `${LAUNCHER_SCHED}` is the scheduling method. You must use 'interleaved' if running with multiple nodes. If on one node, 'dynamic' can be used.
* `${LAUNCHER_WORKDIR}` is the working directory. All jobs will start running here.
* `${LAUNCHER_JOB_FILE}` is the file of jobs you need to create. Each line is a separate job. For example, each job may run a script with a different input.

#### 2. Start the jobs by running this command:
* `paramrun`

## [pylauncher](http://docs.pace.gatech.edu/software/pylauncher/)

Pylauncher uses all features of [Launcher](#launcher) but with additions. You start a small python script to mimic the behavior of Launcher.

