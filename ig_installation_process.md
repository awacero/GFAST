## IG Installation 
### Install dependencies
``` bash
# apt install git
# apt install build-essential 
# apt install libblas-dev liblapack-dev libopenblas-dev libopenblas0 libopenblas64-dev
# apt install liblapacke-dev
# apt install libfftw3-dev 
# apt install gfortran libgfortran5 libgfortran-*-dev
# apt install libhdf5-dev
# apt install libxml2-dev
# apt install swig
# apt install libiniparser-dev
# apt install pkg-config



``` 

### Verify that necesary libraries were installed
``` bash 
find /usr/ -iname libopenblas.so.\*
find /usr/ -iname libCblas.so.\*
find /usr/ -iname libcblas.\*
```

### Download, compile and install ISCL library

``` bash
$ cd
$ mkdir instaladores && cd instaladores
$ git clone https://gitlab.isti.com/bbaker/iscl
$ cd iscl/
$ mkdir build && cd build
$ cmake ..
$ make -j2
$ sudo make install 

```

### Download, compile and install GEOGRAPHICLIB

```bash
git clone https://github.com/geographiclib/geographiclib.git
cd geographiclib/
git checkout r2.0 
mkdir build && cd build
cmake ..
nproc
make -j8
sudo make install

```

### Download, compile and install COMPEARTH

``` bash
cd
mkdir instaladores && cd instaladores
git clone https://github.com/awacero/compearth.git
cd compearth/momenttensor/c_src/
cmake .   -DCBLAS_LIBRARY=/usr/lib/x86_64-linux-gnu/libopenblas.so.0  
make -j8
sudo make install
###Copy the compiled library to the system library folder. 
sudo cp lib/libcompearth_shared.so /usr/local/lib/compearth/

```


```bash
$ cd
$ mkdir instaladores && cd instaladores
$ git clone https://github.com/awacero/GFAST.git
$ mv GFAST gfast


cmake . -DCBLAS_LIBRARY=/usr/lib/x86_64-linux-gnu/libopenblas.so.0 -DGEOLIB_LIBRARY=/home/wilson/instaladores/geographiclib/build/src/libGeographicLib.so
make -j8 VERBOSE=1

cmake . -DCBLAS_LIBRARY=/usr/lib/x86_64-linux-gnu/libopenblas.so.0 -DGEOLIB_LIBRARY=/home/wilson/instaladores/geographiclib/build/src/libGeographicLib.so -DH5_LIBRARY=/usr/lib/x86_64-linux-gnu/hdf5/serial/libhdf5.so -DH5_C_INCLUDE_DIR=/usr/include/hdf5/serial/ -DINIPARSER_INCLUDE_DIR=/usr/include/iniparser/
make -j$(nproc)


```
