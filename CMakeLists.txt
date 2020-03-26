# Copyright (C) 2007-2012 LuaDist.
# Created by Peter Drahoš
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( luaexpat C )
cmake_minimum_required ( VERSION 3.1.3 )
include ( cmake/dist.cmake )
# include ( lua )

# # Find Expat
# find_package ( EXPAT REQUIRED )

include_directories (
    ${EXPAT_INCLUDE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/../lua/src
    ${CMAKE_CURRENT_SOURCE_DIR}/../libexpat/expat/lib
)

# Build LuaExpat module
# install_lua_module ( lxp src/lxplib.c src/lxp.def )
add_library(lxp SHARED src/lxplib.c src/lxp.def )
# find_library(LIBLUA liblua ../lua)
# find_library(EXPAT expat ../libexpat/expat)
target_link_libraries ( lxp 
    expat
    liblua
)

# Install LuaExpat

# install_lua_module ( lxp.lom src/lxp/lom.lua )
# install_data ( README )
# install_doc ( doc/ )
# install_test ( tests/ )

# add_lua_test ( tests/test.lua )
# add_lua_test ( tests/test-lom.lua 
#     ${CMAKE_CURRENT_SOURCE_DIR}/src # workaround to add modules to package.path (improve?)
# )
