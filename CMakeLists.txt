cmake_minimum_required(VERSION 2.6)
find_package(Qt4 REQUIRED QtCore)

if(USE_GPS) #If for GPS usage
  set(USE_RS232 1)
  set(GPS_SRCS gpsreader.cpp) #compile the gps interface
  add_definitions(-DUSE_GPS) #Add a preprocessor define for in code checks for gps usage
  #set(GPS_LIBS qextserialport)
endif(USE_GPS)

include_directories(${QT_INCLUDES} ${CMAKE_CURRENT_BINARY_DIR})
add_definitions(${QT_DEFINITIONS})

set(gpsReader_SRCS gpsreader.cpp)

qt4_automoc(${gpsReader_SRCS})

ADD_LIBRARY(gpsReader STATIC ${gpsReader_SRCS})
	   
TARGET_LINK_LIBRARIES(gpsReader ${qextserialport_LIBRARY} ${QT_QTCORE_LIBRARY})
