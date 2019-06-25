# opencv-ios-framework

`opencv2.framework.zip` 为正常框架

`opencv2-custom.framework.zip` 是去除了与`BaiduMapKit相同的.o文件`，并且重新生成的框架，请自行选择

[opencv2.framework.zip(4.1.0)](https://github.com/Aliveing/opencv-ios-framework/raw/master/opencv2.framework.zip)
[opencv2-custom.framework.zip(4.1.0)](https://github.com/Aliveing/opencv-ios-framework/raw/master/opencv2-custom.framework.zip)

# 关于去除命令：
```shell
    cd opencv2.framework/Versions/A
    lipo -info opencv2 # 查看支持的CPU架构

    # 抽出单个架构的对应文件
    lipo opencv2 -thin armv7 -output cv2.armv7; lipo opencv2 -thin armv7s -output cv2.armv7s; lipo opencv2 -thin arm64 -output cv2.arm64; lipo opencv2 -thin i386 -output cv2.i386; lipo opencv2 -thin x86_64 -output cv2.x86_64;

    # 删除有冲突的.o文件
    ar d cv2.armv7 inflate.o; ar d cv2.armv7 zutil.o; ar d cv2.armv7s inflate.o; ar d cv2.armv7s zutil.o; ar d cv2.arm64 inflate.o; ar d cv2.arm64 zutil.o; ar d cv2.i386 inflate.o; ar d cv2.i386 zutil.o; ar d cv2.x86_64 inflate.o; ar d cv2.x86_64 zutil.o;

    #重新生成opencv2文件
    mv opencv2 opencv2.bak
    lipo -create -output opencv2 cv2.armv7  cv2.armv7s cv2.arm64 cv2.i386 cv2.x86_64;
```
