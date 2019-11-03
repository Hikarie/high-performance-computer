
FC = gfortran
FFLAGS = -fbounds-check -fopenmp
LFLAGS = $(FFLAGS)

.PHONY: plots, clean, clobber

%.o : %.f90
	$(FC) $(FFLAGS) -c $<

SOR2d.exe:  SOR2d_main_omp.o SOR2d_sub_omp.o
	$(FC) $(LFLAGS) SOR2d_main_omp.o SOR2d_sub_omp.o -o $@

solution.txt: SOR2d.exe
	@echo 
	@echo Running code...
	./SOR2d.exe

plots: solution.txt
	@echo 
	@echo Plotting results...
	python plot_solution.py

clean:
	rm -f *.o *.exe

clobber: clean
	rm -f solution.txt *.png

