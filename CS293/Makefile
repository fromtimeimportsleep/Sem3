all: o0 o1 o2 o3

binary: 01-binary.cpp
	g++-11 -std=c++20 -O0 -o binary 01-binary.cpp
	./binary

o0: 02-performance.cpp
	g++-11 -std=c++20 -O0 -o performance-O0 02-performance.cpp
	./performance-O0

o1: 02-performance.cpp
	g++-11 -std=c++20 -O1 -o performance-O1 02-performance.cpp
	./performance-O1

o2: 02-performance.cpp
	g++-11 -std=c++20 -O2 -o performance-O2 02-performance.cpp
	./performance-O2

o3: 02-performance.cpp
	g++-11 -std=c++20 -O3 -o performance-O3 02-performance.cpp
	./performance-O3

alloc:
	g++-11 -std=c++20 03-alloc.cpp
	./a.out > run.data
	gnuplot -persist plot.p

clean:
	rm -rf binary
	rm -rf performance-O0 performance-O1 performance-O2 performance-O3
	rm -rf *~
