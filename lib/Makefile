#
# pg_reorg: lib/Makefile
#
#  Portions Copyright (c) 2008-2012, NIPPON TELEGRAPH AND TELEPHONE CORPORATION
#  Portions Copyright (c) 2011, Itagaki Takahiro
#
MODULE_big = pg_reorg
OBJS = reorg.o pgut/pgut-be.o pgut/pgut-spi.o

EXTENSION = pg_reorg

#supports both EXTENSION (for >=9.1) and without_EXTENSION (for <PG 9.1)
DATA_built = pg_reorg.sql
DATA = pg_reorg--1.0.sql pg_reorg--unpackaged--1.0.sql uninstall_pg_reorg.sql

ifndef USE_PGXS
top_builddir = ../../..
makefile_global = $(top_builddir)/src/Makefile.global
ifeq "$(wildcard $(makefile_global))" ""
USE_PGXS = 1	# use pgxs if not in contrib directory
endif
endif

ifdef USE_PGXS
PG_CONFIG = pg_config
PGXS := $(shell $(PG_CONFIG) --pgxs)
include $(PGXS)
else
subdir = contrib/$(MODULE_big)
include $(makefile_global)
include $(top_srcdir)/contrib/contrib-global.mk
endif

# remove dependency to libxml2 and libxslt
LIBS := $(filter-out -lxml2, $(LIBS))
LIBS := $(filter-out -lxslt, $(LIBS))
