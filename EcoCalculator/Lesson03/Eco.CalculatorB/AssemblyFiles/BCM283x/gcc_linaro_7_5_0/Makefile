ifeq ($(OS), Windows_NT)
	#WINDOWS USE THESE DEFINITIONS
	RM = -del /q /f
	SLASH = \\
	SWALLOW_OUTPUT = >nul 2>nul
else
	#LINUX USE THESE DEFINITIONS
	RM = -rm -f
	SLASH = /
	SWALLOW_OUTPUT =
endif 

# include directories
INC = \
-I ..\..\..\HeaderFiles \
-I ..\..\..\SharedFiles \
-I $(ECO_FRAMEWORK)\Eco.Core1\SharedFiles \
-I $(ECO_FRAMEWORK)\Eco.InterfaceBus1\SharedFiles \
-I $(ECO_FRAMEWORK)\Eco.MemoryManager1\SharedFiles

# source files.
SRC = \
..$(SLASH)..$(SLASH)..$(SLASH)SourceFiles$(SLASH)CEcoCalculatorB.c \
..$(SLASH)..$(SLASH)..$(SLASH)SourceFiles$(SLASH)CEcoCalculatorBFactory.c

OBJ = $(SRC:.c=.o)

OUT = libAE202E543CE54550899603BD70C62565.a
OUT_DIR = ..$(SLASH)..$(SLASH)..$(SLASH)BuildFiles$(SLASH)BCM283x$(SLASH)arm64-v8a$(SLASH)StaticRelease

 
# C++ compiler flags (-g -O2 -Wall)
CCFLAGS = -Wall -O3 -Wno-missing-braces -march=armv8-a+simd -mtune=cortex-a53 -mstrict-align -fno-tree-loop-vectorize -fno-tree-slp-vectorize -DECO_LIB -DECO_BCM283X -DUGUID_UTILITY
 
# compiler
ARMGNU  = $(ECO_TOOLCHAIN)/gcc-linaro-7.5.0/bin/
CCC = $(ARMGNU)aarch64-elf-gcc
 
# library paths
LIBS = -lc -lm -lgcc
 
# compile flags
LDFLAGS = -g

.SUFFIXES: .c

 all: $(OUT)

.c.o:
	$(CCC) $(INC) $(CCFLAGS) -c $< -o $@
 
$(OUT): $(OBJ)
	$(ARMGNU)aarch64-elf-ar -rcs $(OUT_DIR)\$(OUT) $(OBJ)
	$(RM) $(OBJ)

clean:
	$(RM) $(OBJ) $(OUT_DIR)\$(OUT)