
cmake_minimum_required(VERSION 3.10)

project(intw VERSION 0.0.0 LANGUAGES Fortran)

set(CMAKE_VERBOSE_MAKEFILE ON)

find_library(BLAS_LIBRARY
	NAMES blas
	PATHS ENV LD_LIBRARY_PATH
	)
message(${BLAS_LIBRARY})
find_library(BLAS_LIBRARY
        NiAMES refblas
        PATHS ENV LD_LIBRARY_PATH
        )
message(${BLAS_LIBRARY})

#enable_language(Fortran)
#find_package(MPI REQUIRED)
#set ( CMAKE_Fortran_FLAGS "-O2 -xHost")

add_library(mylib STATIC
    src/modules/messages.f90
)

add_executable(
	hello
	src/utils/hello.f90
	# src/messages.f90
)

target_link_libraries(hello PRIVATE mylib)
