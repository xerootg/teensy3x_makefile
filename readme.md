# A simple makefile template for (somewhat) standalone compilation of Teensy projects

cores is submoduled in so teensyduino and arduino are not required.

I use this with a msys environment provided by mingw on Windows

Two options for use:

1) teensyduino/arduino is installed:<br>
    Specify `ARDUINOPATH=/path/to/Arduino` as a make ardument<br><br>
    On Windows this is `/c/Program\ Files\ \(x86\)/Arduino` but msys/mingw make struggles with the space. Make a junction if you want to use the teensyduino/arduino provided arm compilers and tools. `mklink /J c:\arduino "c:\Program Files (x86)\Arduino"`. Once that is done you can specify `ARDUINOPATH=/c/arduino`<br><br>
    On Linux this might be `ARDUINOPATH=/usr/share/arduino`<br><br>
2) make and arm-none-eabi-gcc are installed:<br>
    arm-none-eabi-gcc is the only requirement for compile.<br><br>
    Specify `COMPILERPATH=/path/to/arm-none-eabi/binaries` as a `make` argument if its not in `/usr/bin`<br><br>
    To flash a teensy with the compiled firmware, also specify `TOOLPATH=/path/to/teensy/loader/binaries`

Targets in the makefile:
* clean - cleans everything
* upload - builds the project, and uploads it
* reboot - reboots the teensy
* upload-reboot - runs the upload and reboot targets
* submodule - performs a git submodule checkout for missing repos. This runs by default.