# COOK

* 'cook' is a build system optimized for micro-controller embedded systems.
* 'cook' provides an alternative to the monolithic approach to firmware.
* 'cook' promotes a feature-based modulular approach to multi-target development.
* 'cook' depends upon bash, make, remake, gcc, gdb, openocd

# INSTALLATION

* Include cook/bin folder in you PATH environment variable.
* Copy the contents of cook/settings/home_dot_cook to $HOME/.cook and edit as required.

~~~~
cook --help

cook <switches> [feature]

--project     | -p   [project-dir]
--target      | -t   [target]

--help        | -?   Produce this help text
--state       | -s   Produce listing of current state
--clean       | -c   Clean current project/target/feature
--debug       | -d   Build for debugging and launch gdb
--release     | -r   Build for release
--rebuild     | -R   Clean and Build
--flash       | -f   Flash the target
--features    | -F   List features
--examine     | -x   Examine build steps (requires 'remake')
--environment | -e   List environment variables
--serials     | -S   List serial numbers (export HLA_SERIAL=) 
--verbose     | -v   Verbose Output
--threads     | -T   Compiler Threads
current state:

    project = /home/mike/Documents/GitLabs/afm-10-src
    feature = tcp/httpform
     target = pa2500
 build-kind = release
~~~~


# PROJECT DIRECTORY HIRARCHY

- archives
- bin
- feature
  - _bsp
  - _common
  - _main
- gdb
- ld
- src
  - _bsp


## archives

Placement for archived project settings using the --archive flag.

## bin

Placement for custom shell scrips and executables.

## feature

Placement for top-level features.

## feature/_common

Placement for properties common to all features.

## feature/_common/_bsp.mk
## feature/_common/_feature.mk
## feature/_common/build.mk
## feature/_common/cflags-debug.mk
## feature/_common/cflags-release.mk
## feature/_common/cflags.mk
## feature/_common/clibs.mk
## feature/_common/includes.mk
## feature/_common/ocd.mk
## feature/_common/paths.mk
## feature/_common/tools.mk

## feature/main

Placement for the "final" feature, or application.

## gdb

Placement for debugger scripts and settings.

## ld

Placement for linked scripts.

## src

Placement for source code dependencies.

# ENVIRONMENT VARIABLE

- FEATURE_ROOT
- TARGET
- BUILD_KIND
- CFLAGS_COMMON
- SRC_BSP
- SRCS_CC
- SRCS_CXX
- FEATURE_ROOT
  