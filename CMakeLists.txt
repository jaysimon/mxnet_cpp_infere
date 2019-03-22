cmake_minimum_required(VERSION 3.1)
project(fowl_detect_pic)

set(CMAKE_CXX_STANDARD 11)

find_package( OpenCV REQUIRED )
include_directories(${OpenCV_INCLUDE_DIRS})

set(MXNET_ROOT /home/hw/00-softwares/mxnet/mxnet-1.4)
include_directories(
    ${MXNET_ROOT}/include
    ${MXNET_ROOT}/cpp-package/include
    ${MXNET_ROOT}/mshadow
    ${MXNET_ROOT}/dmlc-core/include
    ${MXNET_ROOT}/nnvm/include
    ${MXNET_ROOT}/dlpack/include
)
link_directories(${MXNET_ROOT}/lib)
set(LIBRARIES mxnet)
add_executable(fowl_detect_pic
    src/main.cpp
    )
target_link_libraries(fowl_detect_pic -lmxnet -lpthread ${OpenCV_LIBS}
    ${LIBRARIES})