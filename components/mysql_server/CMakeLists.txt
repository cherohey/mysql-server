# Copyright (c) 2016, 2017, Oracle and/or its affiliates. All rights reserved.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License, version 2.0,
# as published by the Free Software Foundation.
#
# This program is also distributed with certain software (including
# but not limited to OpenSSL) that is licensed under separate terms,
# as designated in a particular file or component or in included license
# documentation.  The authors of MySQL hereby grant you an additional
# permission to link the program and your derivative works with the
# separately licensed software that they have included with MySQL.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License, version 2.0, for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301  USA

INCLUDE_DIRECTORIES(
  ${CMAKE_SOURCE_DIR}/libbinlogevents/include
)

SET(MYSQL_SERVER_COMPONENT_SOURCES
  registry.cc
  dynamic_loader.cc
  dynamic_loader_path_filter.cc
  server_component.cc
  my_metadata.cc
  my_ref_counted.cc
  mysql_component.cc
  mysql_service_implementation.cc
  dynamic_loader_scheme_file.cc
  plugin_registry_service.cc
  log_builtins.cc
  log_builtins_filter.cc
  mysql_mutex_service.cc
  mysql_rwlock_service.cc
  mysql_cond_service.cc
)

MYSQL_ADD_COMPONENT(mysql_server
	${MYSQL_SERVER_COMPONENT_SOURCES} STATIC)
TARGET_LINK_LIBRARIES(component_mysql_server ${LIBDL} mysys)
ADD_DEPENDENCIES(component_mysql_server GenError)
