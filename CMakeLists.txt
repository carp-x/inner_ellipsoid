cmake_minimum_required(VERSION 3.5)
project(cpp_example)

find_package(Eigen3 REQUIRED)

include_directories(
  include
  /usr/local/include/coin-or
  /usr/include/adolc
  ${EIGEN3_INCLUDE_DIR}
)
link_directories(
  /usr/local/lib
  /usr/lib/adolc
)

add_library(AdolcNLP src/ADOL-C_NLP.cpp)
target_link_libraries(AdolcNLP ipopt adolc)

add_executable(cpp_example src/cpp_example.cpp)
target_link_libraries(cpp_example AdolcNLP ipopt adolc)
