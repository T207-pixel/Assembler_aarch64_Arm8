CROSS_COMPILE ?= aarch64-linux-gnu-

PREFIX = /opt/gcc-linaro-7.5.0-2019.12-x86_64_aarch64-linux-gnu/


AS = $(CROSS_COMPILE)as
LD = $(CROSS_COMPILE)ld



AS_FLAGS = -g
LD_FLAGS = -g -static
LIBPATH = -L $(PREFIX)/lib/gcc/aarch64-linux-gnu/7.5.0 -L $(PREFIX)/aarch64-linux-gnu/libc/usr/lib
OBJPATH = $(PREFIX)/aarch64-linux-gnu/libc/usr/lib
LIBS = -lgcc -lgcc_eh -lc -lm
PREOBJ = $(OBJPATH)/crt1.o $(OBJPATH)/crti.o
POSTOBJ = $(OBJPATH)/crtn.o

SRCS = prog.s
OBJS = $(SRCS:.s=.o)

EXE = prog



all: $(SRCS) $(EXE)


clean:
        rm -rf $(OBJS)


$(EXE): $(OBJS)
        $(LD) $(LD_FLAGS) $(LIBPATH) $(PREOBJ) $(OBJS) $(POSTOBJ) -\( $(LIBS) -\) -o $@



.s.o:
        $(AS) $(AS_FLAGS) $< -o $@

