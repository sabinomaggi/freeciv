### How to compile Freeciv for macOS

0. Add the following lines at the end of the `.gitignore` file:
```
# Specifc additions for macOS version
!freeciv-app/lib/*.a
!freeciv-app/lib/*.la
```

1. Open the Terminal and set the `PKG_CONFIG_PATH` to  
`export PKG_CONFIG_PATH=/usr/local/opt/icu4c/lib/pkgconfig:$PKG_CONFIG_PATH`.

2. Edit the file `autogen.sh` and change line \#16  
from `FC_RUN_CONFIGURE=yes`  
to`FC_RUN_CONFIGURE=no`  
and line \#240  
from  `real_package_name "libtoolize"  "ftp://ftp.gnu.org/pub/gnu/libtool/" 2 2 || DIE=1`  
to `real_package_name "glibtoolize" "ftp://ftp.gnu.org/pub/gnu/libtool/" 2 2 || DIE=1`  

3. From the Terminal, run freeciv's `./autogen.sh` script.

4. If `autogen.sh` ends without errors, run `./configure` with the following options

    `./configure --prefix=$HOME/Development/freeciv-mac/freeciv-app --enable-client=gtk3.22,gtk3,sdl2 --enable-freeciv-manual=html --enable-mapimg=auto --enable-debug=no --enable-static=no`

5. When the configuration script ends, run `make` to compile freeciv, and then run `make install` to install the freeciv binaries in the `freeciv-app` directory.


### How to clean and start again

From the Terminal, run  
    `rm -r freeciv-app`  
    `make distclean`


### How to bundle Freeciv for macOS

1. Copy the `data` directory from the root freeciv directory to the installation directory
    `cp -p -r data ./freeciv-app`

...
