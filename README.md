# QTinyAes
A Qt-Wrapper for the AES-implementation kokke/tiny-AES128-C

This class is simply a wrapper for https://github.com/kokke/tiny-AES128-C. It allows to use the simple AES-implementation inside Qt and with Qt's `QByteArray` class.

## Features
 - It's a C++-class instead of just C-functions
 - Easy integration with Qt-Projects thanks to the use of QByteArray
 - Allows plain-texts of any size - padding will be added automatically
 
## Installation
The package is providet as qpm package, [`de.skycoder42.qtinyaes`](https://www.qpm.io/packages/de.skycoder42.qtinyaes/index.html). To install:

1. Install qpm (See [GitHub - Installing](https://github.com/Cutehacks/qpm/blob/master/README.md#installing), for **windows** see below)
2. In your projects root directory, run `qpm install de.skycoder42.qtinyaes`
3. Include qpm to your project by adding `include(vendor/vendor.pri)` to your `.pro` file

Check their [GitHub - Usage for App Developers](https://github.com/Cutehacks/qpm/blob/master/README.md#usage-for-app-developers) to learn more about qpm.

**Important for Windows users:** QPM Version *0.10.0* (the one you can download on the website) is currently broken on windows! It's already fixed in master, but not released yet. Until a newer versions gets released, you can download the latest dev build from here:
- https://storage.googleapis.com/www.qpm.io/download/latest/windows_amd64/qpm.exe
- https://storage.googleapis.com/www.qpm.io/download/latest/windows_386/qpm.exe

## Example
```cpp
QTinyAes aes;

aes.setMode(QTinyAes::CBC);
aes.setKey("randomkey_128bit");// 128 bit key -> QTinyAes::KEYSIZES must contain the size
aes.setIv("random_iv_128bit");//QTinyAes::BLOCKSIZE

QByteArray plain = "Hello World";
qDebug() << "plain:" << plain
QByteArray cipher = aes.encrypt(plain);
qDebug() << "cipher:" << cipher;
QByteArray result = aes.decrypt(cipher);
qDebug() << "result:" << result;
``
