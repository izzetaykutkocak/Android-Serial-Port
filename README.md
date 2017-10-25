## Android-Serial-Port
安卓串口通讯，基于google官方编译，方便以后使用。

## 说明library
* libs
各类cpu架构对应的so文件

* src/main/android_serialport_api
一些控制类和打开关闭串口的操作

* ByteUtil
工具类，字节转string

* CRC16Verify
crc16校验算法

* OnDataReceiverListener
接受到回复后的回调监听

## 使用
1、将library作为依赖导入
2、如果使用时报错缺少so，请将so文件复制到libs下，并配置
```
 sourceSets {
        main {
            jniLibs.srcDirs = ['libs']
        }
```
3、在module 的build.gradle中添加
```
repositories {
    flatDir {
        dirs 'libs'
    }
}
```
```
dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    androidTestCompile('com.android.support.test.espresso:espresso-core:2.2.2', {
        exclude group: 'com.android.support', module: 'support-annotations'
    })
    compile 'com.android.support:appcompat-v7:26.+'
    testCompile 'junit:junit:4.12'
    compile(name: 'serialport', ext: 'aar')
}
```
### SerialPort
串口操作类，对应jni方法。用于串口打开关闭，获取输入输出流，通过输入输出流发送报文和获取响应报文。

### MachineControl
控制类，打开关闭串口

### SerialFinder 可不使用
串口操作类
枚举所有设备串口

<a target="_blank" href="//shang.qq.com/wpa/qunwpa?idkey=fe261afcf91e31f976ec47fc74c5cc0e1d29843423849dafd78967807aca9f92"><img border="0" src="//pub.idqqimg.com/wpa/images/group.png" alt="Rair修仙开发交流" title="Rair修仙开发交流"></a>

## License
Apache2.0
