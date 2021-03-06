# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
# KIND, either express or implied.  See the License for the
# specific language governing permissions and limitations
# under the License.

if(NEED_LINK_DL)
   set(LIB_DL dl)
endif()

include_directories(${Boost_INCLUDE_DIRS} ../../include)
add_library(common_obj OBJECT $<TARGET_OBJECTS:x_platform_obj> status.cc sasl_digest_md5.cc ioservice_impl.cc options.cc configuration.cc configuration_loader.cc hdfs_configuration.cc uri.cc util.cc retry_policy.cc cancel_tracker.cc logging.cc libhdfs_events_impl.cc auth_info.cc namenode_info.cc statinfo.cc fsinfo.cc content_summary.cc locks.cc config_parser.cc)
add_library(common $<TARGET_OBJECTS:x_platform_obj> $<TARGET_OBJECTS:common_obj> $<TARGET_OBJECTS:uriparser2_obj>)
target_link_libraries(common ${LIB_DL})
target_include_directories(common_obj PRIVATE ../../lib)
target_include_directories(common PRIVATE ../../lib)
