
#include $(CGSLROOT)/src/makefile.inc
FC = ifort
LD = ifort

FCFLAGS = -O2 -xHost -ip -traceback -warn interfaces -assume byterecl -fp-model precise -fp-model source -assume protect_parens
LDFLAGS =

JOB = r8lib_prb.new
TARGET = $(JOB).app

OBJS = jburk_r8lib_sort_.o \
       jburk_r8lib_i4vec_.o \
       jburk_r8lib_r8vec_.o \
       jburk_r8lib_r8row_.o \
       jburk_r8lib_r8col_.o \
       jburk_r8lib_r8mat_.o \
       jburk_r8lib_r8poly_.o \
       r8lib.new.o \
       $(JOB).o

MODS = $(OBJS=:.o=.mod)
SRCS = $(OBJS=:.o=.f90)

.SUFFIXES: .o .f90
%.o: %.f90
	$(FC) $(FCFLAGS) -c $< -o $@

all: $(TARGET)

$(TARGET): $(OBJS)
	$(LD) $(LDFLAGS) -o $(TARGET) $(OBJS)
	rm -f *__genmod.f90
	rm -f *.o *.mod
	chmod 700 $(TARGET)

clean:
	rm -f *__genmod.f90
	rm -f *.app *.o *.mod
	rm -f *.log
