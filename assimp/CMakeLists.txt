FILE(GLOB_RECURSE ASSIMP_SOURCES *.cpp *.c *.cc)
FILE(GLOB_RECURSE ASSIMP_HEADERS *.hpp *.h)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/include 
	${CMAKE_CURRENT_SOURCE_DIR}/code 
	${CMAKE_CURRENT_SOURCE_DIR}/code/BoostWorkaround
	${CMAKE_CURRENT_SOURCE_DIR}/../z)

ADD_DEFINITIONS(
	-DASSIMP_BUILD_NO_C4D_IMPORTER
	-DASSIMP_BUILD_BOOST_WORKAROUND
	-DASSIMP_BUILD_NO_OWN_ZLIB
	"-frtti"
	"-fexceptions")

ADD_LIBRARY(ankiassimp ${ASSIMP_SOURCES} ${ASSIMP_HEADERS})
TARGET_LINK_LIBRARIES(ankiassimp ankiz)
SET_TARGET_PROPERTIES(ankiassimp PROPERTIES LINKER_LANGUAGE CXX)
