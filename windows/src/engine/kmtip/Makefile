#
# KMTIP Makefile
#

!include ..\..\Defines.mak

build: version.res dirs
    $(MSBUILD) kmtip.vcxproj $(MSBUILD_BUILD) /p:Platform=Win32
    $(MSBUILD) kmtip.vcxproj $(MSBUILD_BUILD) /p:Platform=x64
    $(COPY) x86\kmtip.dll $(PROGRAM)\engine
    $(COPY) x64\kmtip64.dll $(PROGRAM)\engine\kmtip64.dll
    $(COPY) x86\kmtip.pdb $(DEBUGPATH)\engine
    $(COPY) x64\kmtip64.pdb $(DEBUGPATH)\engine\kmtip64.pdb

clean: def-clean
    $(MSBUILD) kmtip.vcxproj $(MSBUILD_CLEAN) /p:Platform=Win32
    $(MSBUILD) kmtip.vcxproj $(MSBUILD_CLEAN) /p:Platform=x64

signcode:
    $(SIGNCODE) /d "Keyman Engine Text Service" $(PROGRAM)\engine\kmtip.dll
    $(SIGNCODE) /d "Keyman Engine Text Service" $(PROGRAM)\engine\kmtip64.dll

backup:
    $(WZZIP) $(BUILD)\engine\kmtip.zip x86\kmtip.pdb $(BACKUPDEFAULTS) x86\kmtip.dll
    $(WZZIP) $(BUILD)\engine\kmtip64.zip x64\kmtip64.pdb $(BACKUPDEFAULTS) x64\kmtip64.dll

install:
    cd c:\program files (x86)\common files\keyman\keyman engine 10.0
    #regsvr32 /s /u kmtip.dll
    #regsvr32 /s /u kmtip64.dll
    $(COPY) $(PROGRAM)\engine\kmtip.dll "c:\program files (x86)\common files\keyman\keyman engine 10.0\kmtip.dll"
    $(COPY) $(PROGRAM)\engine\kmtip64.dll "c:\program files (x86)\common files\keyman\keyman engine 10.0\kmtip64.dll"
    #regsvr32 /s kmtip.dll
    #regsvr32 /s kmtip64.dll
    cd $(ROOT)\src\engine\kmtip

!include ..\..\Target.mak
