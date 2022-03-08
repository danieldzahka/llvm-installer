cmake_minimum_required(VERSION 3.15)

project(GTCompilers CXX)

include(ExternalProject)
ExternalProject_Add(MyLLVM
  URL
  https://github.com/llvm/llvm-project/releases/download/llvmorg-11.0.0/llvm-project-11.0.0.tar.xz
  INSTALL_DIR ${CMAKE_CURRENT_BINARY_DIR}/llvm-install
  CMAKE_GENERATOR Ninja
  CMAKE_ARGS
  -DLLVM_USE_LINKER=gold
  -DCMAKE_BUILD_TYPE=RelWithDebInfo
  -DCMAKE_INSTALL_PREFIX=<INSTALL_DIR>
  -DLLVM_ENABLE_PROJECTS=clang
  -DLLVM_TARGETS_TO_BUILD=X86
  -DBUILD_SHARED_LIBS=ON
  -DLLVM_USE_SPLIT_DWARF=ON
  SOURCE_SUBDIR llvm
)
