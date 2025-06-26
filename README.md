# What is ELF32/64 format?
---------------------------------------------------------------------------
ELF stands for (Executable and Linkable Format) it is a standard format developed UNIX System Laboratories in 1990 and is used in UNIX-like systems like Linux, BSD , indicating that a program is an executable among other things(similar to .exe in windows)
programs like gcc(GNU compiler collection) and ld (GNU linker) add this format to object files in order to make them executable on linux

The ELF format also called ELF header is placed in top of the files and it contains different sections with different values

## Sections
### Magic:
it is a unique sequence of numbers that identify that it is an ELF file
0x7f 0x45 0x4c 0x46 

### Class:
indicates which architecture the file is intended for 64-bit or 32-bit
0x01 for ELF32
0x02 for ELF64

### Data:
indicates how signed numbers should be stored in memory (in modren processors it is always 2's complement), and what type of [endianness](https://youtu.be/LxvFb63OOs8?si=O6m39i7gIhJzcwnO) the machine is you are running the program on, x86 and x86_64 machines are little endian

0x01 for little endian
0x02 for big endian

### ELF version:
there is only one version of the standard till date so 

0x01 for version 1

### ABI:
ABI is Application binary interface, it is a set of specification on how programs talk to each other on binary level, a widely used ABI here is System V ABI

0x00 for System V ABI

### ABI version:
version of the standard, in case of System V ABI there is only one version

0x00 for version 0

### Type 
there are mainly 4 types of elf files
-Relocatable files: object files, not linked yet
-executable file (fixed address): executable file but they are loaded at a fixed prespecified address in memory, this is not prefered and usually not used
-Shared library: these are files that contain common functionality that many programs can load share at the same time (similar to DLL in windows)
-position-independent executable(PIE): executable file with a relative prespecified address to be loaded in so the kernel can choose where to load it, this is prefered to use as it provide more security of it's use of [ALSR](https://en.wikipedia.org/wiki/Address_space_layout_randomization)
-Core dump: these are files produced by the kernel when a crash happens, they take a snapshot of the memory layout of a program for debugging purposes

0x01 for relocatable files
0x02 for fixed virtual address executables
0x03 for Position independent executable or shared library
0x04 for core dump

### Machine 
the architecture of the machine you are on
0x3E for x86_64
0xB7 for arm64

### ISA version
there is only one
0x01 for 1

### Entery point address
this is the relative virtual address of the program in memory where main() 

###

