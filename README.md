# linux-binaries
This repository contains linux (linkable) binaries for different linux distributions

## Check if the computer supports OpenGL 3 or OpenGLES.

```
$ glxinfo | grep OpenGL
```

## Prebuilt binaries
We have built x64 OpenGL3 and OpenGLES2 binaries with gcc/g++ 5. 
```
OpenGL3/AURGAViewer
OpenGLES2/AURGAViewer
```
The binaries work in Ubuntu 1604+/Fedora/CentOS/Linux Mint/Kali/PopOS and so on.

If the binaries don't work on your x64 machines. Please try to build ffmpeg and link AURGAViewer by yourself.

## Add udev rules to access raw keyboard/mouse events in userspace

Create udev rules to allow AURGA Viewer to access raw keyboard/mouse device in userspace, otherwise input function will not work in app.
```
$sudo nano /etc/udev/rules.d/99-input-permissions.rules
```
Paste the line in 99-input-permissions.rules
```
KERNEL=="event*", SUBSYSTEM=="input", MODE="0666", GROUP="input"
```
Apply the rules:
```
$sudo udevadm control --reload-rules && sudo udevadm trigger
```

## Install dependencies
For Ubuntu & Debian
```
sudo apt install -y gcc g++ libudev-dev nasm
```

If the graphics card supports OpenGLES2. 

```
sudo apt install -y libgles2-mesa-dev
```

For Redhat/CentOS/Fedora
```
sudo yum install -y gcc g++ make nasm libudev-devel mesa-libGL
```

If the graphics card supports OpenGLES2. 
```
sudo yum install -y mesa-libGLES
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
gcc AURGAViewer.a libmatoya.a libavcodec.a libavutil.a libavformat.a libswscale.a -fPIC -ldl -lpthread -ludev -lm -lstdc++ -o AURGAViewer
```
### For OpenGLES

```
gcc AURGAViewer.a libmatoya.a libavcodec.a libavutil.a libavformat.a libswscale.a -fPIC -lEGL -lGLESv2 -lpthread -ludev -lm -lstdc++ -ldl -o AURGAViewer
```

Run AURGA Viewer
```
./AURGAViewer
```