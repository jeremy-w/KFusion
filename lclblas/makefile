CC=nvcc
CXX=nvcc
CFLAGS=-lOpenCL --profile
CXXFLAGS=-pg -O2
DEPS = check.h reader.h mreader.h sparse-out.h sparse.h
OBJ =  main-out.o reader.o mreader.o sparse-out.o

all: preproc main

preproc: main.cpp sparse.cpp sparse.h kernel.cl
	python ../preprocessor.py main.cpp sparse.cpp kernel.cl

%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS)

main: $(OBJ)
	$(CC) -o $@ $^ $(CFLAGS)
  
clean: 
	rm *.o
	rm main

test: all
	./main 0 1 16 16
