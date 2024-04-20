cmake_minimum_required(VERSION 3.16)

project(SomeIpSniffer VERSION 0.0.1)

set(CMAKE_CXX_STANDARD 17)

include(cmake/CPM.cmake)

set(BUILD_SHARED_LIBS FALSE)
set(CMAKE_POSITION_INDEPENDENT_CODE TRUE)

CPMAddPackage("gh:fmtlib/fmt#10.2.1")
CPMAddPackage("gh:CLIUtils/CLI11@2.4.1")
CPMAddPackage("gh:gabime/spdlog@1.13.0")
CPMAddPackage("gh:nlohmann/json@3.11.3")
CPMAddPackage("gh:catchorg/Catch2@3.5.4")
CPMAddPackage("gh:the-tcpdump-group/libpcap#libpcap-1.10.4")
CPMAddPackage("gh:seladb/PcapPlusPlus@23.09")


add_executable(SomeIpSniffer src/main.cpp)

target_link_libraries(SomeIpSniffer spdlog::spdlog Packet++ Pcap++ CLI11::CLI11 fmt::fmt)


set(CPACK_GENERATOR "RPM;DEB")
set(CPACK_PACKAGE_NAME ${PROJECT_NAME})
set(CPACK_PACKAGE_CONTACT "Mikhail Tsukerman")
set(CPACK_DEBIAN_FILE_NAME DEB-DEFAULT)

include(CPack)
