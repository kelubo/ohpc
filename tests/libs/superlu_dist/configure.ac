#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.
#

AC_PREREQ(2.59)
AC_INIT(superlu_dist, 4.0, karl.w.schulz@intel.com)
AM_INIT_AUTOMAKE([foreign])
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])

# verify we have necessary environment variables set
AC_MSG_CHECKING([for SUPERLU_DIST_DIR environment variable])
if test "x$SUPERLU_DIST_DIR" = "x"; then
   AC_MSG_RESULT([no])
   echo
   AC_ERROR([SUPERLU_DIST_DIR not defined - please load superlu_dist environment.])
else
   AC_MSG_RESULT([no])
fi

# set compilers to use MPI toolchain 
CC=mpicc
CXX=mpicxx
FC=mpif90

# test compilers
AC_PROG_CC
AC_PROG_FC
AC_PROG_RANLIB

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST

CFLAGS="-I ${SUPERLU_DIST_INC} -I ${MKLROOT}/include ${CFLAGS}"
CXXFLAGS="-I ${SUPERLU_DIST_INC} -I ${MKLROOT}/include ${CXXFLAGS} -fopenmp"
FFLAGS="-I ${SUPERLU_DIST_INC} -I ${MKLROOT}/include ${FFLAGS}"
LDFLAGS="-L${METIS_LIB} -L${SUPERLU_DIST_LIB} -lmetis -lsuperlu_dist -L$MKLROOT/lib/intel64 -lmkl_rt -lm ${LDFLAGS}"


# Set subdirectories
AC_CONFIG_FILES(Makefile tests/Makefile)

# Configure
AC_OUTPUT()

echo
echo '-------------------------------------------------- SUMMARY --------------------------------------------------'
echo
echo Package version............... : $PACKAGE-$VERSION
echo OHPC compiler toolchain........ : $LMOD_FAMILY_COMPILER
echo OHPC MPI toolchain............. : $LMOD_FAMILY_MPI
echo
echo C compiler.................... : `which $CC`
echo C++ compiler.................. : `which $CXX`
echo Fortran compiler ............. : `which $FC`
echo 
echo C compiler flags.............. : $CFLAGS
echo C++ compiler flags............ : $CXXFLAGS
echo Fortran compiler flags........ : $FFLAGS
echo 
echo LD flags........ : $LDFLAGS
echo 
echo '-------------------------------------------------------------------------------------------------------------'
