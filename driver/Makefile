################################################################################
#
# Makefile for building driver programs
#
################################################################################

TOPDIR      = $(abspath ../)
BUILD_DIR   = ./.libs
SYSDEP_DIR  = $(TOPDIR)/sysdep

#--------------------------------------------------------

include $(SYSDEP_DIR)/Makedef.$(DCCM_SYS)
include $(TOPDIR)/Mkinclude

COMPO	 = driver
COMPOINC = $(DRIVER_INCLUDEFLAG)
OBJS	 = # mod_$(COMPO).o
MODS	 = # mod_$(COMPO).mod
LIB      = # $(OCNLIB)

TARGETS		= \
	atm_driver ocn_driver \
	dccm_atm_driver dccm_ocn_driver dccm_sfc_driver

TARGETS_PE_NAME = \
	$(ATM_PE_NAME) $(OCN_PE_NAME)            \
	dccm_$(ATM_PE_NAME) dccm_$(OCN_PE_NAME)  \
	dccm_$(SFC_PE_NAME)

# chm_driver

#---------------------------------------------------------

all: $(TARGETS) $(LIBDIR)/$(COMMONLIB) $(BINDIR)
	$(INSTALL) $(TARGETS_PE_NAME) $(BINDIR)
clean:
	$(RM) $(TRASH)
realclean: clean
	$(RM) $(TARGETS)

atm_driver: atm_driver.o $(LIBDIR)/$(ATMLIB)
	$(LINK.f90) -o $(ATM_PE_NAME) $^  $(ATM_LDFLAG) 

ocn_driver: ocn_driver.o $(LIBDIR)/$(OCNLIB)
	$(LINK.f90) -o $(OCN_PE_NAME) $^  $(OCN_LDFLAG) 

dccm_atm_driver: dccm_atm_driver.o $(LIBDIR)/$(ATMLIB)
	$(LINK.f90) -o dccm_$(ATM_PE_NAME) $^  $(ATM_LDFLAG) 

dccm_ocn_driver: dccm_ocn_driver.o $(LIBDIR)/$(OCNLIB)
	$(LINK.f90) -o dccm_$(OCN_PE_NAME) $^  $(OCN_LDFLAG) 

dccm_sfc_driver: dccm_sfc_driver.o $(LIBDIR)/$(SFCLIB)
	$(LINK.f90) -o dccm_$(SFC_PE_NAME) $^  $(SFC_LDFLAG) 


#chm_driver: chm_driver.o $(LIBDIR)/$(CHMLIB)
#	$(LINK.f90) -o $@ $^  $(CHM_LDFLAG)


$(BINDIR):
	mkdir -p $@
