## IG Installation 
### Install dependencies
``` bash
# apt install git build-essential cmake
# apt install libblas-dev liblapack-dev libopenblas-dev libopenblas0 libopenblas64-dev
# apt install liblapacke-dev libfftw3-dev
# apt install gfortran libgfortran5 libgfortran-*-dev
# apt install libhdf5-dev libxml2-dev
# apt install libiniparser-dev pkg-config
### apt install swig



``` 

### Verify that necesary libraries were installed
``` bash 
find /usr/ -iname libopenblas.so.\*
find /usr/ -iname libCblas.so.\*
find /usr/ -iname libcblas.\*
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

### Download, compile and install ISCL library

``` bash
$ cd
$ mkdir instaladores && cd instaladores
$ git clone https://gitlab.isti.com/bbaker/iscl
$ cd iscl/
$ mkdir build && cd build
##Agregar la referencia a la librería compilada antes. 
$ cmake .. \
  -DGEOLIB_LIBRARY=/usr/local/lib/libGeographicLib.so \
  -DGEOLIB_INCLUDE_DIR=/usr/local/include

$ make -j8
$ sudo make install 

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

$ cmake .   -DCBLAS_LIBRARY=/usr/lib/x86_64-linux-gnu/libopenblas.so.0   -DGEOLIB_LIBRARY=/usr/local/lib/libGeographicLib.so  -DH5_LIBRARY=/usr/lib/x86_64-linux-gnu/hdf5/serial/libhdf5.so   -DH5_C_INCLUDE_DIR=/usr/include/hdf5/serial/  -DCOMPEARTH_INCLUDE_DIR=/usr/local/include/   -DCOMPEARTH_LIBRARY=/usr/local/lib/compearth/libcompearth_shared.so -DINIPARSER_INCLUDE_DIR=/usr/include/iniparser/ -DINIPARSER_LIBRARY=/usr/lib/x86_64-linux-gnu/libiniparser.so   -DLIBXML2_INCLUDE_DIR=/usr/include/libxml2   -DLIBXML2_LIBRARY=/usr/lib/x86_64-linux-gnu/libxml2.so



make -j$(nproc)
make install 

```
