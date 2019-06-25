## Android-Serial-Port
Android serial communication, based on google official compilation, convenient for future use.

## Description library
* libs
Libs so files corresponding to various cpu architectures

* src/main/android_serialport_api
Some control classes and operations to turn off the serial port

* ByteUtil
tool class, byte to string

* CRC16Verify
crc16 check algorithm

* BCCVerify
bcc XOR check

* OnDataReceiverListener
receives callback listener after reply

## Usage
1、import the library as a dependency
2、If the error is missing due to use, copy the so file to libs and configure it.
```
 sourceSets {
        main {
            jniLibs.srcDirs = ['libs']
        }
```
3、add in the module's build.gradle

```
dependencies {
    compile(':library')
}
```
### SerialPort
Serial port operation class, corresponding to the jni method. It is used to open and close the serial port, obtain input and output streams, send messages through input and output streams, and obtain response messages.


### SerialPortController
Control class, open and close the serial port, send the acceptance message

Generally written as a singleton, open or close the serial port in the App, do not need to open and close frequently
```
public SerialPortController(String devName, int baudRate) Constructor (serial device name, baud rate)

boolean openCOM()  open the serial port

void setOnDataReceiverListener(OnDataReceiverListener onDataReceiverListener) Sets the listener, receives the reply message and the data length

void closeCOM() closes the serial port

boolean sendCMD(byte[] data) Sends a message
```
### SerialFinder 
can be used
Serial port operation class enumerates all device serial ports

## License
Apache2.0
