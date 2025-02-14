# LINKING
- Es fa servir `-L` a l'hora de compilar per a linkejar llibreries en binari (has d'especificar el directory path començant a buscar des del lloc on estas executant l'accio de compilar, o posar tot el path que et porta des de C:/ (o D:/ o el que sigui) fins la llibreria)\
És a dir `-L <library directory> ` (i aquesta library esta en binari *.dll o similar)

*-L/data[...]/lib*


- Es fa serivr `-l` per a especificar el nom de la llibreria\ És a dir `-L <library name> ` (generalment aixo es fa servir per a les header files, acabades amb `*.h` o `*.c/cpp` o similar)

*-lfoo  # (links libfoo.a or libfoo.so)*

- Es fa servir `-I` per especificar el directori on s'han de buscar les files que s'especifiquen al `#include`

*-I/data[...]/lib*


# PARAMETRES
Els compiladors (GNU compilers, gcc i g++) accepten diversos paràmetres (similar a fer `python -q`).

`-o`  es per especificar el nom de la **o**utput file (`gcc -o hello.exe hello.c`)

`-Wall` es per a que avisi de TOTs els errors (**W**arnings **all**) (`gcc -Wall a.exe a.c`)

`-g` genera informacio adicional que pot anar be a l'hora de fer debugging amb el gdb debugger

`-c` compila el que li donguis a una *object file* és a dir acabada amb `*.o`


# COMBINACIÓ
Obviament tot es pot combinar, si que hi ha una espècie d'ordre en el que s'han de fer les coses però és més aviat una cosa tradicional. Un exemple de compilació és el següent:

`g++ -g -Wall -I/data[...]/lib testing.cpp fileparameters.cpp main.cpp -o test`

# PROCÉS DE COMPILACIÓ PAS A PAS

![Esquema del proces de compilacio](.\Images\compiler_process_esquema.PNG)

Per fer tots aquests passos a la CMD es fa el següent:
1. Preprocessing: AMb el *GNU C preprocessor*, **cpp.exe**, aqui s'inclouen els header files (`#include <>`) i s'expandeixen les macros que s'hagin definit.

    `cpp hello.c > hello.i`

2. Compilation: Es fa servir el compilador amb l'argument `-S` que indica que vols assembly code encomptes de object code

    `g++ -S hello.i`  i obtens la file *hello.s*\
    `gcc -S hello.i`  i obtens la file *hello.s*

3. Assembly: El assembler, **as.exe**, converteis el codi en assembly a machine code (binari), es a dir en extensio *\*.o*

    `as -o hello.o hello.s`

4. Linking: el linker, **ld.exe** linkeja el object code amb les llibreries i produeix un executable file

    `ld -o hello.exe hello.o ...libraries...`



# DIFERENTS TIPUS DE LLIBRERIES I HEADER FILES

- Headers: Acabats amb *.h*
- Static libraries: Acabades amb *.lib*, *.a*
- Shared libraries: Acabades amb *.dll*, *.so*
