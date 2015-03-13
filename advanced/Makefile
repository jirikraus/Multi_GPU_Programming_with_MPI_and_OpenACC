all: run

laplace2d: laplace2d.c common.h laplace2d_serial.h Makefile
	mpicc -fast -acc -ta=nvidia,host laplace2d.c -o laplace2d

clean:
	rm -f laplace2d

run: laplace2d
	mpirun -np 2 ./laplace2d

profile: laplace2d
	mpirun -np 2 nvprof -o laplace2d.%q{OMPI_COMM_WORLD_RANK}.nvvp ./laplace2d
