

set(CMAKE_CXX_STANDARD 17)
SET (CMAKE_CXX_FLAGS " -Wno-deprecated-declarations -fpermissive " CACHE INTERNAL "compiler options" FORCE)
SET (CMAKE_CXX_FLAGS_DEBUG "-O0 -g" CACHE INTERNAL "compiler options" FORCE)
SET (CMAKE_CXX_FLAGS_RELEASE "-O2 -g" CACHE INTERNAL "compiler options" FORCE)
find_library(NUMA_LIB numa REQUIRED)

add_executable(cxlMemTest main.cc test.h util.h workload.h
        test.cc  util.cc  workload.cc)

target_link_libraries(cxlMemTest ${NUMA_LIB} pthread)