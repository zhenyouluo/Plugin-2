PROJECT(PluginExample)
INCLUDE(CollectSrcs)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR})
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/../include)

SET(PluginExample_SUBDIRS .)

GET_SRCS(PluginExample_SRCLISTS PluginExample_SUBDIRS)
ADD_EXECUTABLE(PluginExample ${PluginExample_SRCLISTS})

TARGET_LINK_LIBRARIES(PluginExample boost_filesystem)
TARGET_LINK_LIBRARIES(PluginExample boost_system)
TARGET_LINK_LIBRARIES(PluginExample boost_thread)
TARGET_LINK_LIBRARIES(PluginExample dl)


ADD_SUBDIRECTORY(plugin1)
ADD_SUBDIRECTORY(plugin2)

INSTALL(TARGETS PluginExample
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION bin
    ARCHIVE DESTINATION bin)
