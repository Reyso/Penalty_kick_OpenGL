cmake_minimum_required(VERSION 3.9)
project(Football_Penalty_Shooter)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")
set(OpenGL_GL_PREFERENCE "GLVND") # Adicionar esta linha

find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)

include_directories(${OPENGL_INCLUDE_DIRS} ${GLUT_INCLUDE_DIRS})

set(SOURCE_FILES main.cpp functionalities.cpp shapes.cpp functionalities.h shapes.h constants.h)
FILE(COPY resources DESTINATION "${CMAKE_BINARY_DIR}")

add_executable(Football_Penalty_Shooter ${SOURCE_FILES})
target_link_libraries(Football_Penalty_Shooter ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES})

add_custom_target(run
        COMMAND Football_Penalty_Shooter
        DEPENDS Football_Penalty_Shooter
        WORKING_DIRECTORY ${CMAKE_PROJECT_DIR}
        )
