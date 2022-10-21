# 车牌识别TensorRT

1. 修改CMakeLists.txt  换成你的cuda  tensorrt  以及opencv 路径

   ```
   #cuda 
   include_directories(/mnt/Gu/softWare/cuda-11.0/targets/x86_64-linux/include)
   link_directories(/mnt/Gu/softWare/cuda-11.0/targets/x86_64-linux/lib)

   #tensorrt 
   include_directories(/mnt/Gpan/tensorRT/TensorRT-8.2.0.6/include/)
   link_directories(/mnt/Gpan/tensorRT/TensorRT-8.2.0.6/lib/)
   ```
2. build

   ```
   1. mkdir build
   2. cmake ..
   3. make

   ```
3. onnx 转成tensorrt模型  onnx模型在 onnx_model文件夹   或者自己训练模型看这里[车牌识别](https://github.com/we0091234/Chinese_license_plate_detection_recognition)

   ```
   当前在build目录
   #1 生成检测模型
   ./onnx2trt/onnx2trt  ../onnx_model/plate_detect.onnx ./plate_detect.trt  1
   #2 生成识别模型
   ./onnx2trt/onnx2trt  ../onnx_model/plate_rec.onnx ./plate_rec.trt  1
   ```
4. 推理

   ```
   ./plate_rec ./plate_detect.trt  ./plate_rec.trt ../test_imgs/single_blue.jpg
   ```
   结果保存为了out.jpg
