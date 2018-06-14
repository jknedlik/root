############################################################################
# CMakeLists.txt file for building ROOT net/alien package
# @author Pere Mato, CERN
############################################################################

include_directories(${ALIEN_INCLUDE_DIR} ${XROOTD_INCLUDE_DIRS})
add_definitions(${XROOTD_CFLAGS})


ROOT_GENERATE_DICTIONARY(G__Alien *.h MODULE RAliEn LINKDEF LinkDef.h)

ROOT_ADD_CXX_FLAG(CMAKE_CXX_FLAGS -Wno-shadow)
ROOT_LINKER_LIBRARY(RAliEn *.cxx G__Alien.cxx LIBRARIES ${ALIEN_LIBRARIES} ${XROOTD_LIBRARIES} DEPENDENCIES XMLIO Net Netx NetxNG Tree Proof  )

ROOT_INSTALL_HEADERS()
