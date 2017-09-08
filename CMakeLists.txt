cmake_minimum_required(VERSION 3.0)

Set (HUNTER_ALLOW_SPACES_IN_PATH  ON)
include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.19.80.tar.gz"
    SHA1 "4b72d50fef98189bad4bb098f53bc8893cb46519"
)

project(Foo)

hunter_add_package(Boost COMPONENTS regex system filesystem iostreams)
find_package(Boost CONFIG REQUIRED regex system filesystem iostreams)

add_executable(foo foo.cpp)
target_link_libraries(foo PUBLIC Boost::regex Boost::system Boost::filesystem)


