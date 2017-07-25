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

#### 5. ทำการให้สิทธิแก่ folder
```
$ sudo chown –R user01:user01 /usr/local/hadoop
```

#### 6.สร้าง folder เก็บ log file, data และให้สิทธิแก่ folder
```
$ sudo mkdir /var/log/hadoop
$ sudo chown –R user01:user01 /var/log/hadoop
$ sudo mkdir -p /var/hadoop_data
$ sudo mkdir -p /var/hadoop_data/namenode
$ sudo mkdir -p /var/hadoop_data/datanode
$ sudo chown –R user01:user01 /var/hadoop_data
```

#### 7.แก้ไข .bashrc ด้วย gedit หรือ nano
```
$ gedit .bashrc
```
เพิ่มเข้าไปในไฟล์
```
export HADOOP_HOME=/usr/local/hadoop
export PATH=$PATH:$HADOOP_HOME/bin
export PATH=$PATH:$HADOOP_HOME/sbin
```

#### 8.เข้าไปยัง directory ของ Hadoop เพื่อแก้ไขค่าไฟล์ต่าง ๆ ได้แก่ hadoop-env.sh, yarn-env.sh, core-site.xml, hdfs-site.xml, yarn-site.xml, mapred-site.xml
```
$ cd /usr/local/hadoop/etc/hadoop
```

- hadoop-env.sh
```
$ nano hadoop-env.sh
```
เพิ่ม JAVA_HOME and log directory
```
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export HADOOP_LOG_DIR=/var/log/hadoop
```

- yarn-env.sh
```
$ nano yarn-env.sh
```
เพิ่ม log directory
```
export YARN_LOG_DIR=/var/log/hadoop
```

- core-site.xml
```
$ nano core-site.xml
```
configuration IP address และ  port 9000 ภายใน tag 
```
<configuration>
    <property>
        <name>fs.defaultFS</name>
        <value>hdfs://10.0.2.15:9000</value>
    </property>
</configuration>
```

- hdfs-site.xml
```
$ nano hdfs-site.xml
```
configuration ภายใน tag 
```
<configuration>
  <property>
    <name>dfs.replication</name>
    <value>1</value>
  </property>
  <property>
    <name>dfs.namenode.name.dir</name>
    <value>file:/var/hadoop_data/namenode</value>
  </property>
  <property>
    <name>dfs.datanode.data.dir</name>
    <value>file:/var/hadoop_data/datanode</value>
  </property>
</configuration>
```

- yarn-site.xml
```
$ nano yarn-site.xml
```
configuration ภายใน tag 
```
<configuration>
  <property>
    <name>yarn.resourcemanager.hostname</name>
    <value>10.0.2.15</value>
  </property>
  <property>
    <name>yarn.resourcemanager.scheduler.address</name>
    <value>10.0.2.15:8030</value>
  </property>
  <property>
    <name>yarn.resourcemanager.resource-tracker.address</name>
    <value>10.0.2.15:8031</value>
  </property>
  <property>
    <name>yarn.resourcemanager.address</name>
    <value>10.0.2.15:8032</value>
  </property>
  <property>
    <name>yarn.resourcemanager.admin.address</name>
    <value>10.0.2.15:8033</value>
  </property>
  <property>
    <name>yarn.resourcemanager.webapp.address</name>
    <value>10.0.2.15:8088</value>
  </property>
  <property>
    <name>yarn.nodemanager.aux-services</name>
    <value>mapreduce_shuffle</value>
  </property>
  <property>
    <name>yarn.nodemanager.aux-services.mapreduce.shuffle.class</name>
    <value>org.apache.hadoop.mapred.ShuffleHandler</value>
  </property>
</configuration>
```

- mapred-site.xml
```
$ cp mapred-site.xml.template mapred-site.xml
$ nano mapred-site.xml
```
configuration ภายใน tag 
```
<configuration>
  <property>
    <name>mapreduce.framework.name</name>
    <value>yarn</value>
  </property>
</configuration>
```
#### 9. Format namenode
```
$ hdfs namenode –format
```

#### 10. start
```
$ start-all.sh
$ jps
```

> หากติดตั้งเสร็จสิ้น จะได้ service ทำงาน 6 ตัว ได้แก่ DataNode, NodeManager, NameNode, SecondaryNameNode, ResourceManager, Jps

![service hadoop](/images/day1-1.png)

## Debug
> ถ้าหากพบปัญหา service ไม่ครบ ให้ตรวจสอบดังต่อไปนี้

* Check $nano .bashrc
* Check path ( cd /usr/local/hadoop/etc/hadoop ) 
    * Check $nano hadoop-env.sh
    * Check $nano yarn-env.sh
    * Check $nano core-site.xml
    * Check $nano hdfs-site.xml
    * Check $nano yarn-site.xml
    * Check $nano mapred-site.xml

> ถ้าหากไม่พบ namenode
```
$ stop-all.sh
$ kill -9 process_id ignore jps_process
$ rm –rf /var/hadoop_data/namenode/*
$ rm –rf /var/hadoop_data/datanode/*
$ rm –rf /var/log/hadoop*
$ rm –rf /tmp/hadoop*
$ rm –rf /tmp/Jetty*
$ hdfs namenode –format
$ start-all.sh
$ jps

```