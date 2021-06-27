#Jetpack 4.5 or 4.5.1
# 다운로드 

https://developer.nvidia.com/deepstream-getting-started

로그인하고 약관 동의하면 다운로드 페이지 이동

DeepStream 5.1.0 for Jetson
Download .tar

# 설치 방법

필요한 패키지 설치

$ sudo apt install \
libssl1.0.0 \
libgstreamer1.0-0 \
gstreamer1.0-tools \
gstreamer1.0-plugins-good \
gstreamer1.0-plugins-bad \
gstreamer1.0-plugins-ugly \
gstreamer1.0-libav \
libgstrtspserver-1.0-0 \
libjansson4=2.11-1


Kafka protocol adaptor for message broker 활성화

$ git clone https://github.com/edenhill/librdkafka.git

$ cd librdkafka
$ git reset --hard 7101c2310341ab3f4675fc565f64f0967e135a6a
$ ./configure
$ make
$ sudo make install

$ sudo mkdir -p /opt/nvidia/deepstream/deepstream-5.1/lib
$ sudo cp /usr/local/lib/librdkafka* /opt/nvidia/deepstream/deepstream-5.1/lib

2. extract

cd Downloads

$ sudo tar -xvf deepstream_sdk_v5.1.0_jetson.tbz2 -C /
$ cd /opt/nvidia/deepstream/deepstream-5.1/
$ sudo ./install.sh
$ sudo ldconfig

**********************************************************************

그리고 깃헙 다운로드

git clone https://github.com/katebrighteyes/JetsonDeepStream

그리고 다음 진행


======================================================================
4. Check !!

cd /opt/nvidia/deepstream/deepstream-5.1/sources/objectDetector_SSD

* 참고 ) 즉, 이 위치에서 빌드하고 실행하면 된다.

nvidia@nvidia:/opt/nvidia/deepstream/deepstream-5.0/sources/objectDetector_SSD


export CUDA_VER=10.2

make -C nvdsinfer_custom_impl_ssd

*다운로드 폴더에 label 텍스트와 uff 가 있다면 현재 폴더로 옮겨준다.

cp ~/Downloads/JetsonDeepStream/ssdufftest/* ./

*zip 파일은 풀어준다.
unzip sample_ssd_relu6.zip

ls 
--> sample_ssd_relu6.uff 파일을 확인한다.

*실행
(잊지말자 파워 맥스 밎추고 sudo jetson_clocks !!!)

deepstream-app -c deepstream_app_config_ssd.txt

-----------------------------------------------------

# usb Camera TEST

## Check you usb camera exits and what device number is.

ls /dev/video*

## After check number, you must check 44 line of the "deepstream_app_config_ssd_usb_f32.txt" file 

deepstream-app -c deepstream_app_config_ssd_usb_f32.txt

-----------------------------------------------------------------------
-----------------------------------------------------------------------

# Yolo DeapStream plugin Test

cd /opt/nvidia/deepstream/deepstream-4.0/sources/objectDetector_Yolo

./prebuild.sh

export CUDA_VER=10.2

make -C nvdsinfer_custom_impl_Yolo

deepstream-app -c deepstream_app_config_yoloV3_tiny.txt

deepstream-app -c deepstream_app_config_yoloV2_tiny.txt
  
# If you don't case slow FPS ...

deepstream-app -c deepstream_app_config_yoloV2.txt

deepstream-app -c deepstream_app_config_yoloV3.txt

https://docs.nvidia.com/metropolis/deepstream/dev-guide/text/DS_Quickstart.html#dgpu-setup-for-ubuntu




  




