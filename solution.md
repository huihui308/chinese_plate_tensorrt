
# Error

# error1
```
/usr/include/c++/9/bits/stl_function.h(437): error: identifier "__builtin_is_constant_evaluated" is undefined
```
https://github.com/espressomd/espresso/issues/3654

Solution for the ubuntu-20.04 docker image:
```
apt -y install gcc-8 g++-8
update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 8
update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-8 8
```

Solution for end users:
```
$ mkdir build;cd build
$ rm -rf ./*;cmake -DCMAKE_C_COMPILER=$(which gcc-8) -DCMAKE_CXX_COMPILER=$(which g++-8) -DWITH_CUDA=ON ../;make -j8
```

# error2
```
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasGetPointerMode_v2@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatrixLayoutDestroy@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulPreferenceCreate@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatrixLayoutCreate@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasScopy_v2@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulAlgoCheck@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulPreferenceDestroy@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulAlgoConfigSetAttribute@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasGemmStridedBatchedEx@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmul@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasCreate_v2@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtDestroy@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasSetPointerMode_v2@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulAlgoConfigGetAttribute@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasSasum_v2@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulPreferenceSetAttribute@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatrixLayoutSetAttribute@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulAlgoInit@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasDestroy_v2@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasGemmEx@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulAlgoCapGetAttribute@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasSetStream_v2@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasSetMathMode@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasSscal_v2@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtCreate@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulDescCreate@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasSgemmStridedBatched@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulDescSetAttribute@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulAlgoGetIds@libcublasLt.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasGetMathMode@libcublas.so.11'
/usr/bin/ld: /usr/local/TensorRT-8.2.5.1/lib/libnvinfer_plugin.so.8: undefined reference to `cublasLtMatmulDescDestroy@libcublasLt.so.11'
collect2: error: ld returned 1 exit status
```
<font color=red>Tensorrt 8.2's version must equal cuda version. the cuda version must be 11.4.</font>


