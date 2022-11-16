# WHAT IS 'COOK'?

Cook mainly aims to solve several pervasive problems associated with micro-controller firmware projects.

The first problem that *cook* aims to solve, has to do with the monolithic project model.

The monolithic model which is encouraged by vendor IDEs, discourages modular firmware design, and therefore, also discourages discrete unit testing.

Cook attempts to solve this problem by encouraging a modular design and discrete feature unit tests. A feature is a stand-alone "main()" wrapper around a paticular functional unit.

The second problem that *cook* aims to solve, is that of the the mixed targets. That is, sharing code between multiple targets, and vendors.

* 'cook' is build system optimized for micro-controller firmware projects.
* 'cook' provides an alternative to the monolithic approach to firmware.
* 'cook' promotes a feature-based modulular approach to multi-target development.
* 'cook' depends upon bash, make, remake, gcc, gdb, openocd

# INSTALLATION
```
git checkout https://github.com/8bitgeek/cook.git
git submodule init
git submodule update
sudo ./install.sh
```
* Include the cook/bin folder in you PATH environment variable.
* Copy the contents of cook/settings/home_dot_cook to $HOME/.cook and edit as required.

# SETUP 

FIXME - Add more discription of user settings folder ~/cook.

Personal settings reside in a folder called ~/.cook.

If this folder does not exist, copy the template.
```
cp -r settings/home_dot_cook ~/.cook
```

# USAGE
~~~~
cook --help

cook <switches> [feature]

--archive            Archive workstation settings
--clean       | -c   Clean current project/target/feature
--clone              [target] Clone new target from current target
--debug       | -d   Build for debugging and launch gdb
--environment | -e   List environment variables
--examine     | -x   Examine build steps (requires 'remake')
--features    | -F   List all features
--flash       | -f   Flash the target
--help        | -?   Produce this help text
--openocd     | -o   Start the OpenOCD server independantly
--project     | -p   [project-dir]
--rebuild     | -R   Clean and Build
--release     | -r   Build for release
--remove             [target] Remove an existing target
--restore            [archive] Restore workstation settings
--serials     | -S   List serial numbers (export COOK_SERIAL=) 
--state       | -s   Produce listing of current state
--targets     | -G   List all targets
--target      | -t   [target]
--test        | -E   [test] Build for testing and launch gdb-py
--tui         | -U   Enable debug -tui mode
--threads     | -T   [count] Compiler Threads
--verbose     | -v   Verbose Output
--version     | -V   Display version information
current state:

    project = /home/mike/Documents/GitLabs/afm-10-src
    feature = tcp/httpform
     target = pa2500
 build-kind = release
~~~~


# PROJECT DIRECTORY HIRARCHY

- archives
- _feature
  - _bsp
  - _common
  - main
- gdb
- _ld
- _src
  - _bsp
    - _board 
    - _chip

## ARCHIVES

Personal cook settings may be archived using the cook --archive switch, or restored using the cook --restore switch.

When the the --archive switch is used, the ~/.cook folder is compressed to a file called <hostname>-<username>.tar.gz

By convention, the archive folder can be used to place these compressed settings files, such that they may be preserved in 
the project source code repository, and restored or used as templates at a later time.

## _feature

Top level features are typically discrete stand-alone wrappers to support a library function unit test.

Typical feature tests contain main.c file which contains a "main(..)" function or "feature_main(...)" function.

## _feature/_common

Placement for properties common to all features including build rules and macros.

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

## _ld

Placement for linked scripts.

## _src

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