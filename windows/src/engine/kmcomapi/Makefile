#
# KMCOMAPI Makefile
#

!include ..\..\Defines.mak

build: version.res manifest.res kbd_noicon.res dirs
    gentlb -Tkmcomapi.tlb kmcomapi.ridl
    $(DCC32) kmcomapi.dpr
    $(TDS2DBG) kmcomapi.dll 
    $(MAKEJCLDBG) kmcomapi.map
    $(COPY) kmcomapi.dll $(PROGRAM)\engine
    if exist kmcomapi.dbg $(COPY) kmcomapi.dbg $(DEBUGPATH)\engine

kbd_noicon.res: kbd_noicon.rc
    rc $?

clean: def-clean
    -del kmcomapi.dll
    -del kmcomapi.tlb

signcode:
    $(SIGNCODE) /d "Keyman Engine" $(PROGRAM)\engine\kmcomapi.dll

install:
    regsvr32 /s /u "C:\Program Files (x86)\Common Files\Keyman\Keyman Engine 10.0\kmcomapi.dll"
    $(COPY) $(PROGRAM)\engine\kmcomapi.dll "C:\Program Files (x86)\Common Files\Keyman\Keyman Engine 10.0"
    regsvr32 "C:\Program Files (x86)\Common Files\Keyman\Keyman Engine 10.0\kmcomapi.dll"

backup:
    $(WZZIP) $(BUILD)\engine\kmcomapi.zip  $(BACKUPDEFAULTS) kmcomapi.dll

!include ..\..\Target.mak
