
cmake_minimum_required(VERSION 3.8)
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()
project("CryptoPPProject")
set(CRYPTOPP_DIR "path/to/cryptopp890")
file(GLOB CRYPTOPP_SRC
    "${CRYPTOPP_DIR}/*.cpp"
)
include_directories(${CRYPTOPP_DIR})
add_library(cryptlib STATIC ${CRYPTOPP_SRC})
add_executable(CryptoPPProject "CryptoPPProject.cpp" "CryptoPPProject.h")
target_link_libraries(CryptoPPProject cryptlib)
if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET CryptoPPProject PROPERTY CXX_STANDARD 20)
endif()
