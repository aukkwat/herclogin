# This file is part of Hercules.
# http://herc.ws - http://github.com/HerculesWS/Hercules
#
# Copyright (C) 2012-2016  Hercules Dev Team
# Copyright (C)  Athena Dev Teams
#
# Hercules is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

# src/tool/Makefile.  Generated from Makefile.in by configure.

CONFIG_D = ../config
CONFIG_H = $(wildcard $(CONFIG_D)/*.h) $(wildcard $(CONFIG_D)/*/*.h)

COMMON_D = ../common
COMMON_H = $(filter-out %.p.h, $(wildcard $(COMMON_D)/*.h))
SYSINFO_INC = $(COMMON_D)/sysinfo.inc
COMMON_INCLUDE = -I..

THIRDPARTY_D = ../../3rdparty
THIRDPARTY_INCLUDE = -I$(THIRDPARTY_D)

LIBCONFIG_D = $(THIRDPARTY_D)/libconfig
LIBCONFIG_OBJ = $(addprefix $(LIBCONFIG_D)/, libconfig.o grammar.o scanctx.o \
                scanner.o strbuf.o)
LIBCONFIG_H = $(addprefix $(LIBCONFIG_D)/, libconfig.h grammar.h parsectx.h \
              scanctx.h scanner.h strbuf.h wincompat.h)

MAPCACHE_OBJ = obj_all/mapcache.o
MAPCACHE_C = mapcache.c
MAPCACHE_H =
MAPCACHE_DEPENDS = $(MAPCACHE_OBJ) $(COMMON_D)/obj_all/common_mini.a $(LIBCONFIG_OBJ $(SYSINFO_INC))



CC = gcc
export CC

#####################################################################
.PHONY: all mapcache clean buildclean help

all: mapcache Makefile

mapcache: ../../mapcache

../../mapcache: $(MAPCACHE_DEPENDS) Makefile
	@echo "	LD	$(notdir $@)"
	@$(CC)   -L/usr/local/lib -rdynamic -fno-omit-frame-pointer -o ../../mapcache $(MAPCACHE_DEPENDS) -lpcre -lz 

buildclean:
	@echo "	CLEAN	tool (build temp files)"
	@rm -rf obj_all/*.o

clean: buildclean
	@echo "	CLEAN	tool"
	@rm -rf ../../mapcache

help:
	@echo "possible targets are 'mapcache' 'all' 'clean' 'help'"
	@echo "'mapcache'   - mapcache generator"
	@echo "'all'        - builds all above targets"
	@echo "'clean'      - cleans builds and objects"
	@echo "'buildclean' - cleans build temporary (object) files, without deleting the"
	@echo "               executables"
	@echo "'help'       - outputs this message"

#####################################################################

Makefile: Makefile.in
	@$(MAKE) -C ../.. src/tool/Makefile

$(SYSINFO_INC): $(MAPCACHE_C) $(MAPCACHE_H) $(COMMON_H) $(CONFIG_H) $(LIBCONFIG_H)
	@echo "	MAKE	$@"
	@$(MAKE) -C ../.. sysinfo

obj_all:
	@echo "	MKDIR	obj_all"
	@-mkdir obj_all

obj_all/%.o: %.c $(MAPCACHE_H) $(COMMON_H) $(CONFIG_H) $(LIBCONFIG_H) | obj_all
	@echo "	CC	$<"
	@$(CC) -g -O2 -pipe -ffast-math -Wall -Wextra -Wno-sign-compare -std=c99 -Wno-unused-parameter -Wempty-body -Wnewline-eof -Wint-conversion -Winit-self -Wpointer-arith -Wswitch-bool -Wenum-conversion -Wshorten-64-to-32 -Wconstant-conversion -Wbool-conversion -Wformat-security -Wformat -Wformat-y2k -Wmissing-include-dirs -Wundef -Wnested-externs -Wold-style-definition -Woverlength-strings -Wredundant-decls -Wcast-qual -Wnull-dereference -Wno-format-nonliteral -Wno-switch -Wno-missing-field-initializers -Wshadow -fno-strict-aliasing -g -fno-omit-frame-pointer -DHAVE_EXECINFO -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -D__EXTENSIONS__=1 -D_ALL_SOURCE=1 -D_GNU_SOURCE=1 -D_POSIX_PTHREAD_SEMANTICS=1 -D_TANDEM_SOURCE=1 -DHAVE_USELOCALE=1 -DHAVE_NEWLOCALE=1 -DHAVE_FREELOCALE=1 -DHAVE_XLOCALE_H=1 -DHAVE_EXECINFO_H=1 $(COMMON_INCLUDE) $(THIRDPARTY_INCLUDE)  -DMAXCONN=16384 -I../common -I/usr/local/include -DHAS_TLS -DHAVE_SETRLIMIT -DHAVE_STRNLEN -DPACKETVER=20120410 -DDEBUG -DDISABLE_RENEWAL -DHAVE_MONOTONIC_CLOCK -c $(OUTPUT_OPTION) $<

# missing common object files
$(COMMON_D)/obj_all/common_mini.a:
	@echo "	MAKE	$@"
	@$(MAKE) -C $(COMMON_D) common_mini

$(LIBCONFIG_OBJ):
	@echo "	MAKE	$@"
	@$(MAKE) -C $(LIBCONFIG_D)
