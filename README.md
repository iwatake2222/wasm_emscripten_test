
# About
Convert C++ project to HTML+JS using WASM (Emscripten)

# ビルド方法
```sh
sudo service docker start
docker pull emscripten/emsdk:3.1.1

docker create  -v /mnt/c/iwatake/devel:/root/devel -v /etc/localtime:/etc/localtime:ro -e DISPLAY="192.168.1.2:0"  -w /root/ -p 8888:8888 -it --name=emscripten_01 emscripten/emsdk:3.1.1
docker start emscripten_01
docker exec -it emscripten_01 bash

mkdir build && cd build
emcmake cmake ..
make
```

```sh
sudo service docker start
docker pull emscripten/emsdk:3.1.1

docker run \
  --rm \
  -v $(pwd):/src \
  -u $(id -u):$(id -g) \
  emscripten/emsdk:3.1.1 \
  sh ./build_emscripten.sh
```


