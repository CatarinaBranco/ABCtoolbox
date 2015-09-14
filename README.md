ABCtoolbox
==========

A fork of the ABCtoolbox project from:
[http://www.cmpg.iee.unibe.ch/content/softwares__services/computer_programs/abctoolbox/index_eng.html](http://www.cmpg.iee.unibe.ch/content/softwares__services/computer_programs/abctoolbox/index_eng.html)

Reference:
Wegmann D, Leuenberger C , Neuenschwander S &amp; Excoffier L (2010) ABCtoolbox: a versatile toolkit for approximate Bayesian computations. BMC Bioinformatics 11: 116

# Building
This project should be meta-built together. As in, run CMake against the root CMakeLists.txt file, instead of the individual target lists files. For example:

[user@machine ~]$ cd repos/ABCToolbox  
[user@machine ~/repos/ABCToolbox]$ cmake -H. -Bbuild  
[user@machine ~/repos/ABCToolbox]$ cmake --build ./build  

This will show where the executables are.  
[user@machine ~/repos/ABCToolbox]$ find ./build/source -type f -perm +111 -print

You are welcome to meta-build and build each target individually, but that could lead to bad things and we don't support it.

# Supported Platforms
This project will work on OS X and linux operating systems, but will not work on Windows. The forking code would need to be rewritten, or paramater combination vectors could be extracted and used by a custom pipeline. If you need this to work on Windows, let me know. If you fix it yourself, please send a pull request so I can update the code for everyone else.

