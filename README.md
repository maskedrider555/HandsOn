# HandsOn

## 기본 설정  
Ubuntu : 20.04  
Nvidia Driver : 510.73.05   
Cuda : 11.2  
Cudnn : 8.1.0.77  

## Anaconda 가상환경  
Python : 3.7  
Tensorflow : 2.7.0  

# CUDA 설치
## 1. Nvidia Driver 설치
### 추천 드라이버 확인
ubuntu-drivers devices  
![image](https://user-images.githubusercontent.com/41985798/171995277-73017b66-8bab-41c3-9720-ad74c49226aa.png)  
### 추천 드라이버 설치  
sudo apt install nvidia-driver-510
## 2. CUDA
### CUDA Toolkit 설치
https://developer.nvidia.com/cuda-toolkit-archive 
![image](https://user-images.githubusercontent.com/41985798/171995438-4f608d4a-047f-4e07-9dff-b25a51ad40ca.png)  
wget https://developer.download.nvidia.com/compute/cuda/11.2.0/local_installers/cuda_11.2.0_460.27.04_linux.run  
sudo sh cuda_11.2.0_460.27.04_linux.run 

Driver 제외하고 설치  
![image](https://user-images.githubusercontent.com/41985798/171995517-1e803ced-4cc1-488f-a8af-819013ba300d.png)  
### CUDA 환경변수 설정
nano .bashrc  

다음 문장 추가  
export CUDADIR=/usr/local/cuda  
export PATH=$PATH:$CUDADIR/bin  
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CUDADIR/lib64  
## CUDNN 
### CUDNN 다운로드
https://developer.nvidia.com/rdp/cudnn-archive  
### CUDNN 설치 
tar -xvf cudnn-11.1-linux-x64-v8.0.4.30.tgz  
sudo cp ./cuda/include/* /usr/local/cuda/include/  
sudo cp -P ./cuda/lib64/* /usr/local/cuda/lib64/  
sudo chmod a+r /usr/local/cuda/lib64/libcudnn*  

# Anaconda 설치 
## 1. Anaconda 다운로드
https://www.anaconda.com/products/distribution#Downloads  
## 2. Anaconda 설치
bash Anaconda3-2022.05-Linux-x86_64.sh  
source ~/.bashrc  
## 3. 환경변수 등록
nano ~/.bashrc  
export PATH=$PATH:/home/somnode/anaconda3/bin  
## 4. 가상환경 설정
conda env remove --n DL  
conda create -n DL python=3.7  
conda activate DL  
pip install --upgrade "protobuf<=3.20.1"  
pip install jupyter  
pip install tensorflow==2.7.0  
pip install scikit-learn  
pip install matplotlib  
