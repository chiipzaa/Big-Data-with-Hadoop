# การติดตั้ง SQOOP


#### ดาวโหลดไฟล์มาไว้ก่อนนะครับ
* source : http://sqoop.apache.org/

#### แตกไฟล์ที่ได้ ย้าย และให้สิทธิ
```{bash}
$ tar -xvf sqoop-1.4.6.bin__hadoop-0.23.tar.gz
$ sudo cp -r ./sqoop-1.4.6.bin__hadoop-0.23 /usr/local/sqoop
$ sudo chown -R user01:user01 /usr/local/sqoop

```

#### แก้ไข .bashrc
```
$ nano .bashrc
```
เพิ่มเข้าไปในไฟล์
```
export SQOOP_HOME=/usr/local/sqoop
export PATH=$PATH:$SQOOP_HOME/bin
```
เสร็จแล้ว refresh ด้วยคำสั่ง
```
$ source .bashrc
```
#### แก้ไขค่า config
```
$  cd /usr/local/sqoop/conf/
$  cp sqoop-env-template.sh sqoop-env.sh
$ nano sqoop-env.sh
```
เพิ่มเข้าไป
```
export HADOOP_COMMAND_HOME=/usr/local/Hadoop
export HADOOP_MAPRED_HOME=/usr/local/hadoop
```

#### ติดตั้ง mysql connector
```
$ cd
$ sudo cp mysql-connector-java-5.0.8/mysql-connector-java-5.0.8-bin.jar /usr/local/sqoop/lib 
```

### ตรวจสอบการติดตั้ง หากสำเร็จจะแสดง version ของ sqoop
```
$ sqoop-version
```


 
