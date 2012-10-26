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
