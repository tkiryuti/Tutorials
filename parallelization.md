# Parallelization in PACE

## Options
* [Job Arrays](#job-arrays)
* [GNU Parallel](#gnu-parallel)
* [Launcher](#launcher)
* [pylauncher](#pylauncher)

## When to use each type of Parallelization

## [Job Arrays](http://docs.pace.gatech.edu/software/arrayGuide/)

## [GNU Parallel](http://docs.pace.gatech.edu/software/multiparallel/)

### Important things to note about GNU Parallel
* It is recommended to run only on one node. As of Jan 2021, PACE has 24 processors per each node. Using remote execution to run on more than one node is possible, but we ran into multiple issues with this including a long time for the actual tasks to start and some tasks being dropped and not completed.
* Check out the [tutorial from the GNU Parallel website](https://www.gnu.org/software/parallel/parallel_tutorial.html).
* Load the PACE module `module load parallel` and see documentation with `man parallel`.

To see PACE's example of using GNU Parallel, run the command below. 
It will create a directory with an example PBS batch file and a README file with more details.
```bash
pace-getexample gnu_parallel
```

## [Launcher](http://docs.pace.gatech.edu/software/launcher/)

### Important things to note about Launcher
* It is preferred by PACE over using [Job Arrays](#job-arrays).
* It assumes that we are using the same number of cores on each node.
* It only supports single-core jobs (i.e. each subjob must run only on one processor).
* Jobs can run in any order so there must not be dependencies between jobs.
* It will run as many jobs are the nodes times processors per node (ppn) you request. For example, to run 120 jobs you can request `nodes=5:ppn=24`.

To see PACE's example of using Launcher, run the command below. 
It will create a directory with an example PBS batch file and a README file with more details.
```bash
pace-getexample launcher
```

### Summary of Launcher usage

#### 1. Load the PACE module.
* `module load launcher`

#### 2. Set 3 different environment variables.
* `${LAUNCHER_SCHED}` is the scheduling method. You must use 'interleaved' if running with multiple nodes. If on one node, 'dynamic' can be used.
* `${LAUNCHER_WORKDIR}` is the working directory. All jobs will start running here.
* `${LAUNCHER_JOB_FILE}` is the file of jobs you need to create. Each line is a separate job. For example, each job may run a script with a different input.

#### 3. Start the jobs by running this command.
* `paramrun`

## [pylauncher](http://docs.pace.gatech.edu/software/pylauncher/)

Pylauncher uses all features of [Launcher](#launcher) but with additions. You start a small python script to mimic the behavior of Launcher.

