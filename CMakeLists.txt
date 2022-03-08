cmake_minimum_required(VERSION 3.15)

project(GTCompilers CXX)

include(ExternalProject)
ExternalProject_Add(MyLLVM
  URL
  https://github.com/llvm/llvm-project/releases/download/llvmorg-11.0.0/llvm-project-11.0.0.tar.xz
  INSTALL_DIR ${CMAKE_CURRENT_BINARY_DIR}/llvm-install
  CMAKE_ARGS
  -G "Ninja"
  -D LLVM_USE_LINKER=gold
  -D CMAKE_BUILD_TYPE=RelWithDebInfo
  -D CMAKE_INSTALL_PREFIX=<INSTALL_DIR>
  -D LLVM_ENABLE_PROJECTS="clang;compiler-rt"
  -D LLVM_TARGETS_TO_BUILD=X86
  -D BUILD_SHARED_LIBS=ON
  -D LLVM_USE_SPLIT_DWARF=ON
  SOURCE_SUBDIR llvm
)
