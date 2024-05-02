The source code is contained in the src folder:
* `main.c` is the main file.
* `evolution.c` contains functions used for the evolution of the game.
* `read_write_pgm_image.c` contains functions used to manage pgm files.

# Compilation
To compile the program:
```
srun -n 1 make all
```
# Run
The code can be run using `mpirun`, the input parameters are:
* -i initialize a playground 
* -r run a playground
* -k _num. value_ playground size
* -e[0|1] evolution type: 0 ordered, 1 static
* -f name of the file to be read or written
* -n _num. value_ number of steps to be calculated
* -s _num. value_ every how many steps a dump of the system is saved on file. (0 to save only at the end)

### Initialization
Before starting the game an initial image is created and the command to do so is:
```
mpirun -np 1 main.x -i -k 1000 -f initial
```
This will create a pgm file name initial.pgm that contains a playground of size 1000x1000

### Evolution
An example of a run:
```
mpirun -np 2 main.x -r -f initial -n 100 -e 1 -s 0
```
This will run the static evolution using 2 MPI processes. The initial.pgm file is used as the initial playground, it will evolve for a 100 steps and dump the system only at the end.
