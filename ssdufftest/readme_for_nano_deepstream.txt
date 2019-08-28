1. visit the website and download deepstream_sdk_v4.0_jetson.tbz2

https://developer.nvidia.com/deepstream-download

DeepStream 4.0 for Jetson
Download .tar

2. extract

tar -jxvf deepstream_sdk_v4.0_jetson.tbz2 

3. Install Dependency

sudo apt-get update

sudo apt --fix-broken install

sudo apt-get install     libssl1.0.0     libgstreamer1.0-0     gstreamer1.0-tools     gstreamer1.0-plugins-good     gstreamer1.0-plugins-bad     gstreamer1.0-plugins-ugly     gstreamer1.0-libav     libgstrtspserver-1.0-0     libjansson4

sudo apt-get install librdkafka1=0.11.3-1build1

export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH

4. Install DeepStream

cd


sudo mv Downloads/deepstream_sdk_v4.0_jetson ./

cd deepstream_sdk_v4.0_jetson/
sudo tar -xvf binaries.tbz2 -C /
sudo ./install.sh
sudo ldconfig

5. Check !!

ls /opt/nvidia/deepstream/deepstream-4.0/sources/
cd /opt/nvidia/deepstream/deepstream-4.0/sources/

export CUDA_VER=10.0

make -C nvdsinfer_custom_impl_ssd

*다운로드 폴더에 label 텍스트와 uff 가 있다면 현재 폴더로 옮겨준다.
cp ~/Downloads/JetsonDeepStream-master/ssdufftest/* ./
ls

*실행
deepstream-app -c deepstream_app_config_ssd.txt


nvidia@nvidia:/opt/nvidia/deepstream/deepstream-4.0/sources/objectDetector_SSD
