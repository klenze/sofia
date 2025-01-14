# Create a library called "libR3BSofSci" which includes the source files given in
# the array. The extension is already found. Any number of sources could be listed here.

Set(SYSTEM_INCLUDE_DIRECTORIES
${SYSTEM_INCLUDE_DIRECTORIES}
${BASE_INCLUDE_DIRECTORIES}
)

set(INCLUDE_DIRECTORIES
#put here all directories where header files are located
${R3BROOT_SOURCE_DIR}/r3bbase
${R3BROOT_SOURCE_DIR}/r3bdata
${R3BROOT_SOURCE_DIR}/r3bdata/mwpcData
${R3BROOT_SOURCE_DIR}/tracking
${R3BSOF_SOURCE_DIR}/sofdata
${R3BSOF_SOURCE_DIR}/sofdata/sciData
${R3BSOF_SOURCE_DIR}/tcal
${R3BSOF_SOURCE_DIR}/sci
)

include_directories( ${INCLUDE_DIRECTORIES})
include_directories(SYSTEM ${SYSTEM_INCLUDE_DIRECTORIES})

set(LINK_DIRECTORIES
${ROOT_LIBRARY_DIR}
${FAIRROOT_LIBRARY_DIR}
)

link_directories( ${LINK_DIRECTORIES})

set(SRCS
#Put here your sourcefiles
R3BSofSci.cxx
R3BSofSciContFact.cxx
R3BSofSciRawPosPar.cxx
R3BSofSciRawTofPar.cxx
R3BSofSciMapped2TcalPar.cxx
R3BSofSciTcal2RawPosPar.cxx
R3BSofSciTcal2RawTofPar.cxx
R3BSofSciCalPosPar.cxx
R3BSofSciCalTofPar.cxx
R3BSofSciSingleTcal2CalPosCaveCPar.cxx
R3BSofSciMapped2Tcal.cxx
R3BSofSciTcal2SingleTcal.cxx
R3BSofSciSingleTcal2Cal.cxx
R3BSofSciSingleTcal2Hit.cxx
)

# fill list of header files from list of source files
# by exchanging the file extension
CHANGE_FILE_EXTENSION(*.cxx *.h HEADERS "${SRCS}")

set(LINKDEF SofSciLinkDef.h)
set(LIBRARY_NAME R3BSofSci)
set(DEPENDENCIES
    R3BData R3BSofTcal R3BSofData R3BTracking)

GENERATE_LIBRARY()
