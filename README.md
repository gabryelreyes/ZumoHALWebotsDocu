# ZumoHALWebots <!-- omit in toc -->

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](http://choosealicense.com/licenses/mit/)
[![Repo Status](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip)
[![Release](https://img.shields.io/github/release/BlueAndi/ZumoHALWebots.svg)](https://github.com/BlueAndi/ZumoHALWebots/releases)

Hardware abstraction layer for the Pololu Zumo robot (see https://www.pololu.com/category/129/zumo-robots-and-accessories) in the Webots simulation.

## Table of content

* [Architecture](#architecture)
  * [The Principle](#the-principle)
  * [Detail](#detail)
* [How to integrate the library?](#how-to-integrate-the-library)
* [Used Libraries](#used-libraries)
* [Issues, Ideas And Bugs](#issues-ideas-and-bugs)
* [License](#license)
* [Contribution](#contribution)

# Architecture

## The Principle
![Principle](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/BlueAndi/ZumoHALWebots/master/doc/uml/Principle.plantuml)

## Detail
![HAL](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/BlueAndi/ZumoHALWebots/master/doc/uml/HAL.plantuml)

See details of the Webots library classes in the [Webots reference manual](https://cyberbotics.com/doc/reference/nodes-and-api-functions).

# How to integrate the library?
1. Add it to the _platformio.ini_ in your environment to the _lib\_deps_ section:
    ```
    lib_deps =
        BlueAndi/ZumoHALWebots @ ~0.1.1
    ```
2. Add to your platformio environment the following scripts.
    ```
    extra_scripts =
        pre:$PROJECT_LIBDEPS_DIR/$PIOENV/ZumoHALWebots/scripts/create_webots_library.py
        pre:$PROJECT_LIBDEPS_DIR/$PIOENV/ZumoHALWebots/scripts/copy_sounds.py
        post:$PROJECT_LIBDEPS_DIR/$PIOENV/ZumoHALWebots/scripts/copy_webots_shared_libs.py
    ```
    * ```create_webots_library.py```: Generates the Webots library under the ```/lib``` folder, derived from your local Webots installation.
    * ```copy_sounds.py```: Copies the sound files used for sound generation.
    * ```copy_webots_shared_libs.py```: Copies the Webots shared libraries to the local platformio environment specific build folder ```.pio/build/<environment>``` as post-build step. They are required by the exectuable.

# Used Libraries

| Library                                                            | Description                                                      | License    |
| ------------------------------------------------------------------ | ---------------------------------------------------------------- | ---------- |
| [ArduinoJson](https://github.com/bblanchon/ArduinoJson)            | JSON library for Arduino and embedded C++. Simple and efficient. | MIT        |
| [Webots](https://github.com/cyberbotics/webots)                    | Webots physical simulation C++ API.                              | Apache 2.0 |
| [ZumoHALInterfaces](https://github.com/BlueAndi/ZumoHALInterfaces) | The Zumo C++ HAL interfaces.                                     | MIT        |

# Issues, Ideas And Bugs
If you have further ideas or you found some bugs, great! Create a [issue](https://github.com/BlueAndi/ZumoHALWebots/issues) or if you are able and willing to fix it by yourself, clone the repository and create a pull request.

# License
The whole source code is published under the [MIT license](http://choosealicense.com/licenses/mit/).
Consider the different licenses of the used third party libraries too!

# Contribution
Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, shall be licensed as above, without any
additional terms or conditions.
