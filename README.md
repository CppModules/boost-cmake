# boost

基于cmake的boost静态库项目
> 当前版本基于  
> [Boost 1.85.0](https://www.boost.org/users/history/version_1_85_0.html)  
> April 15th, 2024 17:38 GMT

如何使用?

```
$ git submodule add https://github.com/OpenHYGUI/boost-cmake modules/projects/boost
```

然后在主项目的 CMakeLists.txt 里加入

```
set(Boost_USE_STATIC_LIBS ON)
set(Boost_USE_STATIC_RUNTIME ON)

find_package(Boost 1.85 COMPONENTS thread system filesystem program_options random atomic chrono)
if (NOT Boost_FOUND)
add_subdirectory(modules/projects/boost)
include_directories(modules/projects/boost)
endif()
```

最后给你的项目链接上

```
target_link_libraries(target_project ${BOOST_LIBRARIES})
```

## Cmake选项

| 宏                       | 注释                   |
|-------------------------|----------------------|
| USE_BOOST_SERIALIZATION | Boost::serialization |
| USE_BOOST_LOCALE        | 是否引入Boost::locale    |
| USE_BOOST_FIBER         | 是否引入Boost::fiber     |