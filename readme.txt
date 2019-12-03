2019. 10.16 기준
1. Jetpack 4.2.1 이상에서만 Xavier, TX2, Nano 가 모두 DS 가능

2. Tx2, Nano 의 경우 4.2.1 + DS 4.0 (다운로드 버전) -> 정상 동작

3. Xavier, TX2, Nano 모두 4.2.2 + DS 4.0.1 (다운로드 버전)-> 정상 동작


따라서 추후에는 아래와 같이 사이트에서 다운받아서 사용하도록 한다.

1. visit the website and download deepstream_sdk_v4.0_1_jetson.tbz2

https://developer.nvidia.com/deepstream-download

DeepStream 4.0 for Jetson
Download .tar

2. extract

tar -jxvf deepstream_sdk_v4.0.1_jetson.tbz2 

**********************************************************************

하지만 지금은 scp 로 받아서 사용해야합니다. !!!!

cd Downloads

(화이트보드 참고)
scp nvidia@[아이피]:/home/nvidia/TOD/deepstream_sdk_v4.0_jetson.zip .

unzip deepstream_sdk_v4.0_jetson.zip -d deepstream_sdk_v4.0_jetson

그리고 깃헙 다운로드

git clone https://github.com/katebrighteyes/JetsonDeepStream

그리고 다음 진행

3. Install Dependency

sudo apt-get update

sudo apt --fix-broken install

sudo apt-get install     libssl1.0.0     libgstreamer1.0-0     gstreamer1.0-tools     gstreamer1.0-plugins-good     gstreamer1.0-plugins-bad     gstreamer1.0-plugins-ugly     gstreamer1.0-libav     libgstrtspserver-1.0-0     libjansson4

sudo apt-get install librdkafka1=0.11.3-1build1

export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH

======================================================================
4. Install DeepStream

cd

sudo mv Downloads/deepstream_sdk_v4.0.1_jetson ./

cd deepstream_sdk_v4.0.1_jetson/
sudo tar -xvf binaries.tbz2 -C /
sudo ./install.sh
sudo ldconfig

5. Check !!

cd /opt/nvidia/deepstream/deepstream-4.0/

ls

sudo chmod 777 ./

cp -rf ~/deepstream_sdk_v4.0.1_jetson/sources ./
cp -rf ~/deepstream_sdk_v4.0.1_jetson/samples/ ./
ls

cd /opt/nvidia/deepstream/deepstream-4.0/sources/objectDetector_SSD

* 참고 ) 즉, 이 위치에서 빌드하고 실행하면 된다.

nvidia@nvidia:/opt/nvidia/deepstream/deepstream-4.0/sources/objectDetector_SSD


export CUDA_VER=10.0

make -C nvdsinfer_custom_impl_ssd

*다운로드 폴더에 label 텍스트와 uff 가 있다면 현재 폴더로 옮겨준다.

cp ~/Downloads/JetsonDeepStream-master/ssdufftest/* ./

*zip 파일은 풀어준다.
mv sample_ssd_relu6/sample_ssd_relu6.uff ./

ls 
--> sample_ssd_relu6.uff 파일을 확인한다.

*실행
(잊지말자 파워 맥스 밎추고 sudo jetson_clocks !!!)

deepstream-app -c deepstream_app_config_ssd.txt
