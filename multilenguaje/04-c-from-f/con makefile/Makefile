.PHONY: default help object executable all clean

CC = gcc

LDC = $(CC)

FC = gfortran

LDF = $(FC)

SOURCE_F = $(wildcard *.f90)

OBJECTS_F = $(patsubst %.f90, %_f90.o, $(SOURCE_F))

SOURCE_C = $(wildcard *.c)
OBJECTS_C = $(patsubst %.c, %_c.o, $(SOURCE_C))

EXECUTABLE = f-main-c.e

objectsF: $(OBJECTS_F)

objectsC: $(OBJECTS_C)

executable: $(EXECUTABLE)

all: objectsC objectsF executable

%_f90.o: %.f90
	$(FC) -c $^ -o $@

%_c.o: %.c
	$(CC) -c $^ -o $@

%.e: $(OBJECTS_F) $(OBJECTS_C)
	$(LDF) $^ -o $@

clean:
	rm -rfv $(OBJECTS_F) $(OBJECTS_C) $(EXECUTABLE)
