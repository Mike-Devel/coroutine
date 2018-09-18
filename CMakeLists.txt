cmake_minimum_required(VERSION 3.8)
project(boost-coroutine LANGUAGES CXX)

if (WIN32)
    set(OS windows)
else()
    set(OS posix)
endif()

add_library(boost_coroutine
    src/exceptions.cpp
    src/detail/coroutine_context.cpp
    src/${OS}/stack_traits.cpp
)
add_library(Boost::coroutine ALIAS boost_coroutine)

target_include_directories(boost_coroutine PUBLIC include)

target_link_libraries(boost_coroutine
    PUBLIC
        Boost::assert
        Boost::config
        Boost::context
        Boost::core
        Boost::exception
        Boost::move
        Boost::range
        Boost::system
        Boost::throw_exception
        Boost::type_traits
        Boost::utility
        Boost::winapi
)
