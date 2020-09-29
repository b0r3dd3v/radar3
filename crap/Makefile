# This file is part of Quipper. Copyright (C) 2011-2019. Please see the
# file COPYRIGHT for a list of authors, copyright holders, licensing,
# and other details. All rights reserved.
# 
# ======================================================================

# TOP-LEVEL MAKEFILE FOR QUIPPER

LIBRARIES:=src/Quipper/Utils src/Quipper/Libraries

ALGORITHMS:=src/Quipper/Algorithms/BF src/Quipper/Algorithms/BWT	\
       src/Quipper/Algorithms/CL src/Quipper/Algorithms/GSE		\
       src/Quipper/Algorithms/QLS src/Quipper/Algorithms/TF		\
       src/Quipper/Algorithms/USV

PROGRAMS:=src/Quipper/Programs/QCLParser src/Quipper/Programs/Tools

DEMOS:=src/Quipper/Demos src/Quipper/Demos/Template

SUBDIRS:=src $(LIBRARIES) $(ALGORITHMS) $(PROGRAMS) $(DEMOS)

# ----------------------------------------------------------------------
# Default rule

.PHONY: all fast
.PHONY: $(SUBDIRS)

all: 
	$(MAKE) SUBDIR_TARGET=all $(FAST) $(SUBDIRS)

$(SUBDIRS):
	$(MAKE) $(FAST) -C "$@" $(SUBDIR_TARGET)

src: src/Quipper/Utils
src/Quipper/Libraries: src/Quipper/Utils src
$(ALGORITHMS): src $(LIBRARIES)
$(PROGRAMS): src $(LIBRARIES)
$(DEMOS): src $(LIBRARIES) $(ALGORITHMS)


# ----------------------------------------------------------------------
# Faster compilation: "make fast <target>" will skip optimization

FAST := 
fast: 
	$(eval FAST := fast)

# ----------------------------------------------------------------------
# Cleaning

tidy:
	$(MAKE) SUBDIR_TARGET=tidy $(FAST) $(SUBDIRS)

clean:
	$(MAKE) SUBDIR_TARGET=clean $(FAST) $(SUBDIRS)
