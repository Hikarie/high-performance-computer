
FC = gfortran
FFLAGS = -fbounds-check -fopenmp
LFLAGS = $(FFLAGS)

.PHONY: plots, clean, clobber

%.o : %.f90
	$(FC) $(FFLAGS) -c $<

redblack2d.exe:  redblack2d_main_omp.o redblack2d_sub_omp.o
	$(FC) $(LFLAGS) redblack2d_main_omp.o redblack2d_sub_omp.o -o $@

solution.txt: redblack2d.exe
	@echo 
	@echo Running code...
	./redblack2d.exe

plots: solution.txt
	@echo 
	@echo Plotting results...
	python plot_solution.py

clean:
	rm -f *.o *.exe

clobber: clean
	rm -f solution.txt *.png

