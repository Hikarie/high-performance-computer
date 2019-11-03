
FC = gfortran
FFLAGS = -fbounds-check -fopenmp
LFLAGS = $(FFLAGS)

.PHONY: plots, clean, clobber

%.o : %.f90
	$(FC) $(FFLAGS) -c $<

golden2d.exe:  golden2d_main_omp.o golden2d_sub_omp.o
	$(FC) $(LFLAGS) golden2d_main_omp.o golden2d_sub_omp.o -o $@

solution.txt: golden2d.exe
	@echo 
	@echo Running code...
	./golden2d.exe

plots: solution.txt
	@echo 
	@echo Plotting results...
	python plot_solution.py

clean:
	rm -f *.o *.exe

clobber: clean
	rm -f solution.txt *.png

