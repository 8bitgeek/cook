# cook

* cook build system for unix-like environments 
* dependencies; bash, make, remake, gcc, gdb, openocd

INSTALLATION

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