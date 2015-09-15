cmake_minimum_required(VERSION 3.2 FATAL_ERROR )

project(cutecom)

cmake_policy(SET CMP0020 NEW)

find_package(Qt5Core REQUIRED)
find_package(Qt5Widgets REQUIRED)
find_package(Qt5SerialPort REQUIRED)

include_directories(${QT_INCLUDES} ${CMAKE_BINARY_DIR})
set(cutecomSrcs main.cpp qcppdialogimpl.cpp)

set(CMAKE_AUTOMOC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOUIC ON)

set(binInstallDir bin)

add_executable(cutecom ${cutecomSrcs} ${uiHeaders})
target_link_libraries(cutecom Qt5::Widgets Qt5::Core Qt5::SerialPort)

install(TARGETS cutecom DESTINATION ${binInstallDir} )

install(FILES cutecom.1 DESTINATION share/man/man1 )
