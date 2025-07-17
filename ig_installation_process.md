## IG Installation 
### Install dependencies
``` bash 
# apt install libblas-dev liblapack-dev libopenblas-dev libopenblas0 libopenblas64-dev
# apt install liblapacke-dev
# apt install libiniparser-dev
# apt install gfortran libgfortran5 libgfortran-*-dev
# apt install libhdf5-dev
# apt install libxml2-dev
# apt install swig


``` 

### Verify that necesary libraries were installed
``` bash 
find /usr/ -iname libopenblas.so.\*
find /usr/ -iname libCblas.so.\*
find /usr/ -iname libcblas.\*
```




```bash
$ cd
$ mkdir instaladores && cd instaladores
$ git clone https://github.com/awacero/GFAST.git
$ mv GFAST gfast

```
