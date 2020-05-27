# A short explaination about the `.sh` file

```
#!/bin/bash

#               Filename                   Coord       Channel  Cali          Bg   RFI  Wgt  TS  Raw LSS Pho Apt   Ann   Finding  Loc Trm M10
../RDP/RDP.out  ../images/<filename>.fits  equatorial  left     interpolated  6.0  0.7  0.33 1   0   0   0   1.25  5.0   center   0   0   0

#   source          destination
cp  ./SSS_main.txt  <filename>.txt

```

The syntax above is fairly straight forward: both are calling an application (called an _executable_ in the context of linux), 
then we give the application a list of options (called _arguments_) separated by one or more white spaces. The application is always
the first thing in a line. Here `../RDP/RDP.out` is an application that "we" wrote and thus must be specified with a path to
itself, while `cp` (short for "copy") is an application that the system provides us as a utility, so no need to provide its path.

The order by which we give an application its argument is purely dependent on the application itself. I.e. it is defined within the
application code, and there's generally no way for us to change the ordering of arguments except for changing the source code of the
application itself. Here we have the comments above each line indicating which argument that we are providing ("Coord", "Channel", etc.).
Note that these comments are not giving instructions to the application about which argument is which, but to simply remind ourselves 
which argument is at what position, so removing these comments won't affect the functionality of this script or the application.

When referencing any file—either an _executable_ (as an application) or a normal file (as an argument for an application)—we often use
`.` and `..` to indicate relative paths, so that we don't have to type the whole path out (e.g., we can use `../images` instead of
`/not_backed_up/oj287/images`). The two symbols for relative paths are:

* `..` indicates going back to the parent folder
* `.` indicates the current folder. We use `.` to reduce the ambiguity when refering to an executable/normal file. For example,
we used the system utility `cp` above to copy a file. But what if we want to reference a file, in the current folder, that also has
the name `cp`? Then we will use `./cp` to make clear we are referencing the file in the current folder.

Following the discussion above, when we want to run our customized `run.sh` script, it is important that we add the `.`, i.e. we use
`./run.sh` instead of `run.sh`. This is because when we call an application, the system goes to a set of locations where applications
are often installed to look for the application we call. Since our `run.sh` executable is not part of the system, it cannot find it
unless we provide an explicit path (like what we did when we called `RDP.out`).