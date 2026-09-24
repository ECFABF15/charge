cmake_minimum_required(VERSION 3.10.0)
project(charge VERSION 0.1.0 LANGUAGES C)

# 查找ncurses（这一段必须放在add_executable前面！）
set(CURSES_NEED_NCURSES TRUE)
set(CURSES_NEED_WIDE TRUE)
find_package(Curses REQUIRED)

add_executable(charge charge.c 汉化.h)

# 链接库
target_link_libraries(charge PRIVATE ${CURSES_LIBRARIES})
target_include_directories(charge PRIVATE ${CURSES_INCLUDE_DIRS})

install(TARGETS charge DESTINATION bin)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)