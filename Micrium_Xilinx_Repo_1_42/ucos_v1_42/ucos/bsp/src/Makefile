#########################################################################################################
#                                           MICRIUM XSDK REPOSITORY
#                          (c) Copyright 2014-2015; Micrium, Inc.; Weston, FL
#
#               All rights reserved.  Protected by international copyright laws.
#########################################################################################################

COMPILER=
CP=cp
COMPILER_FLAGS=
EXTRA_COMPILER_FLAGS=
LIB=libucos.a

include ../../../include/Makefile_def.inc
include Makefile.inc

CC_FLAGS = $(COMPILER_FLAGS)
ECC_FLAGS = $(EXTRA_COMPILER_FLAGS)

RELEASEDIR=../../../lib
INCLUDEDIR=../../../include
INCLUDES=-I./. -I${INCLUDEDIR}

OUTS = *.o

LIBSOURCES:=ucos_startup.c \
            ucos_shell_init.c \
            ucos_fs_init.c \
            ucos_tcpip_init.c \
            ucos_dhcp-c_init.c \
            ucos_dns-c_init.c \
            ucos_http-c_init.c \
            ucos_mqtt-c_init.c \
            ucos_telnet-s_init.c \
            ucos_iperf_init.c \
            ucos_usbd_init.c \
            ucos_usbh_init.c \
            ucos_openamp_init.c \
            ucos_stdinout.c \
            ucos_printf.c \
            
LIBSOURCES += $(ARCH_LIBSOURCES)

INCLUDEFILES:=app_cfg.h \
              ucos_bsp.h \
              ucos_int.h
              
INCLUDEFILES += $(ARCH_INCLUDEFILES)
              

OBJECTS =	$(addsuffix .o, $(basename ${LIBSOURCES}))

libs: banner ucos_ucos_libs clean

%.o: %.c
	${COMPILER} $(CC_FLAGS) $(ECC_FLAGS) $(INCLUDES) -o $@ $<

%.o: %.S
	${COMPILER} $(CC_FLAGS) $(ECC_FLAGS) $(INCLUDES) -o $@ $<

banner:
	echo "Compiling uC/OS"

ucos_ucos_libs: ${OBJECTS}
	$(ARCHIVER) -r ${RELEASEDIR}/${LIB} ${OBJECTS}

.PHONY: include
include:
	${CP} ${INCLUDEFILES} ${INCLUDEDIR}

clean:
	rm -rf ${OBJECTS}

