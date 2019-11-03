
FC = gfortran
FFLAGS = -fbounds-check -fopenmp
LFLAGS = $(FFLAGS)

.PHONY: plots, clean, clobber

%.o : %.f90
	$(FC) $(FFLAGS) -c $<

gauss2d.exe:  gauss2d_main_omp.o gauss2d_sub_omp.o
	$(FC) $(LFLAGS) gauss2d_main_omp.o gauss2d_sub_omp.o -o $@

solution.txt: gauss2d.exe
	@echo 
	@echo Running code...
	./gauss2d.exe

plots: solution.txt
	@echo 
	@echo Plotting results...
	python plot_solution.py

clean:
	rm -f *.o *.exe

clobber: clean
	rm -f solution.txt *.png

