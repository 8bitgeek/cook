# COOK

* 'cook' is a build system optimized for micro-controller embedded systems.
* 'cook' provides an alternative to the monolithic approach to firmware.
* 'cook' promotes a feature-based modulular approach to multi-target development.
* 'cook' depends upon bash, make, remake, gcc, gdb, openocd

# INSTALLATION
```
git submodule init
git submodule update
```

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
  - main
- gdb
- ld
- src
  - _bsp


## archives

Placement for archived project settings using the --archive flag.

## bin

Placement for custom shell scrips and executables.

## feature

Placement for top-level features. Features are stand-alone executables.
Features must have a main() function.

## _feature/_common

Placement for properties common to all features.

## _feature/_common/_bsp.mk
## _feature/_common/_feature.mk
## _feature/_common/build.mk
## _feature/_common/cflags-debug.mk
## _feature/_common/cflags-release.mk
## _feature/_common/cflags.mk
## _feature/_common/clibs.mk
## _feature/_common/includes.mk
## _feature/_common/ocd.mk
## _feature/_common/paths.mk
## _feature/_common/tools.mk

## _feature/_main

By convention, placement for the "final" feature, or application.

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

# TARGET PROJECT ENVIRONMENT VARIABLES

```
ENV_OPENOCD_INTERFACE=ftdi/um232h
ENV_OPENOCD_TARGET=gd32vf103
ENV_OPENOCD_ADAPTER_SPEED=1000
ENV_GCC_ROOT=/opt/riscv-gcc/bin/
ENV_GCC_PREFIX=$(ENV_GCC_ROOT)/riscv32-unknown-elf-
ENV_GCC_LIB=/../lib/gcc/riscv32-unknown-elf/10.1.0
ENV_LIB_GCC=$(ENV_GCC_ROOT)$(ENV_GCC_LIB)/libgcc.a
ENV_LIB_M=$(ENV_GCC_ROOT)/../riscv32-unknown-elf/lib/libm.a
ENV_LIB_GPP=$(ENV_GCC_ROOT)/../riscv32-unknown-elf/lib/libstdc++.a
```

# ORDER OF OPERATIONS

Top level makefile.

MAKE_FEATURE=$MAKE_PATH/$FEATURE_MK


# SUBLIME TEXT BUILD 

```
cook.sublime-build:

{
  "shell_cmd": "cook",
  "file_regex": "^\\s*(\\S[^:]*).(\\d+):(\\d+)"
}

```