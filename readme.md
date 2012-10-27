mpi-cluster
======
Build an MPI cluster. First, install software.

    # Install mpi on the master (localhost)
    mpi-cluster build localhost

    # Install mpi on two slave boxes.
    mpi-cluster build root@host1.domain not_root@host2.domain

Then configure slaves; run this on the master.

    # Add two slaves on username@host1.domain
    mpi-cluster add username@host1.domain 2
    
    # Add four slaves on username@host1.domain
    mpi-cluster add username@host2.domain 4

## Running R
(Directions come from [here](http://support.rstudio.org/help/discussions/questions/618-using-rstudio-server-with-rmpi-and-an-mpi-cluster).)

Run something like this to open an interactive R session with access to the
cluster.

    mpirun --hostfile .mpi_hostfile -np 1 R --no-save --interactive

Then, from the session,

    library(Rmpi)
    cl <- mpi.spawn.Rslaves(nslaves=1)                  

And register it with `foreach` (from [here](http://cran.r-project.org/web/packages/doMPI/vignettes/doMPI.pdf))

    library(doMPI)
    registerDoMPI(cl)
