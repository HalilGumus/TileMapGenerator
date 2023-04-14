cmake_minimum_required(VERSION 3.25)
project(TileMapGenerator)

set(CMAKE_CXX_STANDARD 23)

add_executable(TileMapGenerator main.cpp)

find_package(SDL2 CONFIG REQUIRED)
target_link_libraries(TileMapGenerator
        PRIVATE
        $<TARGET_NAME_IF_EXISTS:SDL2::SDL2main>
        $<IF:$<TARGET_EXISTS:SDL2::SDL2>,SDL2::SDL2,SDL2::SDL2-static>
        )

find_package(SDL2_image CONFIG REQUIRED)
target_link_libraries(TileMapGenerator PRIVATE $<IF:$<TARGET_EXISTS:SDL2_image::SDL2_image>,SDL2_image::SDL2_image,SDL2_image::SDL2_image-static>)