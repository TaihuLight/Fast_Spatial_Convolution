CFLAGS = -std=c11 -Ofast

fastMatrixMultiplication : Main.c Time.o Mem_Alloc.o Spatial_Convolution.o Global_Setting.h	
	gcc $(CFLAGS) Main.c Time.o Mem_Alloc.o Spatial_Convolution.o -o fastMatrixMultiplication


oclFastMatrixMultiplicaton : cl_main.c Time.o Mem_Alloc.o Global_Setting.h
	gcc $(CFLAGS) -framework OpenCL -std=c11 cl_main.c Mem_Alloc.c Time.c -o oclFastMatrixMultiplicaton
#	gcc generate_matrix_data.c -lopenblas -o fastMatrixMultiplication -std=c11 -Ofast


Time.o : Time.h Time.c
	gcc $(CFLAGS) -c Time.c


Spatial_Convolution.o : Spatial_Convolution.h Spatial_Convolution.c Mem_Alloc.o Global_Setting.h
	gcc $(CFLAGS) -c Spatial_Convolution.c


Alloc_Mem.o : Mem_Alloc.h Mem_Alloc.c
	gcc $(CFLAGS) -c Mem_Alloc.c


.PHONY : exec
exec :
	./fastMatrixMultiplication
	./oclFastMatrixMultiplicaton


.PHONY : clean
clean :
	-rm fastMatrixMultiplication Time.o Mem_Alloc.o Spatial_Convolution.o oclFastMatrixMultiplicaton
