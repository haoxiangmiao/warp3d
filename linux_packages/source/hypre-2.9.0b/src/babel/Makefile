#BHEADER**********************************************************************
# Copyright (c) 2008,  Lawrence Livermore National Security, LLC.
# Produced at the Lawrence Livermore National Laboratory.
# This file is part of HYPRE.  See file COPYRIGHT for details.
#
# HYPRE is free software; you can redistribute it and/or modify it under the
# terms of the GNU Lesser General Public License (as published by the Free
# Software Foundation) version 2.1 dated February 1999.
#
# $Revision: 2.18 $
#EHEADER**********************************************************************





include ../config/Makefile.config

# Python support.
# It is very important that you keep the Python modules up-to-date.
# They contain copies of hypre binaries taken from the libraries
# libHYPRE.so and libbHYPRE.so.
# When you first run make at the top level (linear_solvers directory),
# the libraries get built before the Python modules, so all is well.
# But if you later change something and rebuild in a subdirectory, the Python
# modules won't get automatically updated.  You need to cd to babel, and
# type "make" there too.

# The build process for the Python interface can be time- and space-consuming,
# so we don't want to do it unless requested.
ifeq ($(BUILD_PYTHON),1)
   BHYPRE_BABEL_PYTHON_DIR=bHYPREClient-P
endif
# The build process for the Java interface has environment variable requirements
# which many people may not have satisfied, so we don't want to do it unless
# requested.
ifeq ($(BUILD_JAVA),1)
   BHYPRE_BABEL_JAVA_DIR=bHYPREClient-J
endif

BHYPRE_BABEL_DIRS =\
 bHYPRE \
 bHYPREClient-C\
 bHYPREClient-F\
 bHYPREClient-CX\
 $(BHYPRE_BABEL_JAVA_DIR)\
 $(BHYPRE_BABEL_PYTHON_DIR)

HYPRE_BABEL_RUNTIME_SIDL_DIR = ${HYPRE_SRC_TOP_DIR}/babel-runtime/sidl

HYPRE_BABEL_RUNTIME_PYTHON_DIR = ${HYPRE_SRC_TOP_DIR}/babel-runtime/python

all:
	@ \
	for i in ${BHYPRE_BABEL_DIRS}; \
	do \
	  if [ -d $$i ]; \
	  then \
	    echo "Making $$i ..."; \
	    (cd $$i && $(MAKE) $@); \
	  fi; \
	done
	cp -fpPR ${HYPRE_BABEL_RUNTIME_SIDL_DIR}/*.h ${HYPRE_BUILD_DIR}/include
	cp -fpPR hypre_babel_exception_handler.h ${HYPRE_BUILD_DIR}/include
	cp -fpPR ${HYPRE_BABEL_RUNTIME_SIDL_DIR}/.libs/libs*${HYPRE_LIB_SUFFIX} ${HYPRE_BUILD_DIR}/lib

install:
	@ \
	for i in ${BHYPRE_BABEL_DIRS}; \
	do \
	  if [ -d $$i ]; \
	  then \
	    echo "Making $$i ..."; \
	    (cd $$i && $(MAKE) $@); \
	  fi; \
	done
	cp -fpPR ${HYPRE_BABEL_RUNTIME_SIDL_DIR}/*.h ${HYPRE_INC_INSTALL}
	cp -fpPR hypre_babel_exception_handler.h ${HYPRE_INC_INSTALL}
	cp -fpPR ${HYPRE_BABEL_RUNTIME_SIDL_DIR}/.libs/libs*${HYPRE_LIB_SUFFIX} ${HYPRE_LIB_INSTALL}

clean:
	@ \
	for i in ${BHYPRE_BABEL_DIRS}; \
	do \
	  if [ -d $$i ]; \
	  then \
	    (cd $$i && $(MAKE) $@); \
	  fi; \
	done

distclean:
	@ \
	for i in ${BHYPRE_BABEL_DIRS}; \
	do \
	  if [ -d $$i ]; \
	  then \
	    (cd $$i && $(MAKE) $@); \
	  fi; \
	done

