# Big data with Hadoop 

## Resource
- http://ftp.psu.ac.th/pub/bigdata
- http://bit.ly/2srgho0 

## Day 1:
Download: Ubuntu.zip, VirtualBox-5.1.22-115126-Win.exe

#### Step by Step
1.	Install VirtualBox and Unzip Ubuntu.zip
2.	Create VM with VirtualBox select type: Linux (64bits) mem=>4gb Using Exit HDD from download
>Tip: Exit Full Screen VirtualBox (Right CTRL + F)

#### Big data Definition
- Volume
- Varity
- Velocity
- Veracity


## Installation

>In VM Ubuntu: user: user01 password: password
### steb by step

##### 1. ติดตั้ง java
```
 $ sudo apt-get install openjdk-8-jdk
```
> การตรวจสอบว่ามี java แล้วหรือยังด้วย
> $ java -version

##### 2. เพิ่ม PATH ของ java ลงใน .bashrc
```
$ nano .bashrc
```
เพิ่มเข้าไปในไฟล์
```
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export PATH=$PATH:$JAVA_HOME/bin
```

#### 3. Download Hadoop
source : http://hadoop.apache.org/releases.html
ณ ตอนที่ทำใช้ version 2.7.3
แตก zip ไฟล์ที่ download มาด้วย
```
$ tar –xvf hadoop-2.7.3.tar.gz
```

#### 4. ย้าย folder ที่เก็บไว้ยัง /usr/local/Hadoop
```
$ sudo mv ./hadoop-2.7.3 /usr/local/hadoop
```

