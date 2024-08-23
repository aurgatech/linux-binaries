# ClearOS binaries
This directory contains compiled binaries and linkable files.

## Check if the computer supports OpenGL 3 or OpenGLES.

```
$ glxinfo | grep OpenGL
```

## Install dependencies
```
sudo yum install -y make nasm libudev-devel devtoolset-11-gcc.x86_64 devtoolset-11-gcc-c++.x86_64 
```

if the computer supports OpenGL 3+
```
sudo yum install -y mesa-libGL
```

if the computer supports OpenGL ES2.0+
```
sudo yum install -y mesa-libGLES
```

## Append the following line to end of ~/.bashrc 
```
export PATH=/opt/rh/devtoolset-11/root/usr/bin/:$PATH
```
Apply the changes
```
source ~/.bashrc 
```

## Build ffmpeg
```
wget https://ffmpeg.org/releases/ffmpeg-6.0.tar.xz
```

```
tar xvf ffmpeg-6.0.tar.xz
```
```
./configure --prefix=output --enable-shared --enable-static --disable-programs --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-swresample --disable-postproc --disable-avfilter --disable-network  --disable-avdevice --disable-everything --enable-decoder=h264
```

```
make & make install
```

Copy libavcodec.a libavutil.a libavformat.a libswscale.a from output/lib/ to AURGA Viewer's build folder with AURGAViewer.a & libmatoya.a.

## Link AURGA Viewer

### For OpenGL 3
```
cd x64-OpenGL3
```
```
gcc AURGAViewer.a libmatoya.a libavcodec.a libavutil.a libavformat.a libswscale.a -fPIC -lEGL -lGLESv2 -lpthread -ludev -lm -lstdc++ -ldl -o AURGAViewer
```
### For OpenGLES
```
cd x64-OpenGLES
```

```
gcc AURGAViewer.a libmatoya.a libavcodec.a libavutil.a libavformat.a libswscale.a -fPIC -ldl -lpthread -ludev -lm -lstdc++ -o AURGAViewer
```

Run AURGA Viewer
```
./AURGAViewer
```