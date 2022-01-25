
# About
- Sample project to:
- Convert C++ project to HTML+JS using WebAssembly(WASM) + Emscripten
- Deploy the compiled pages using GitHub Actions
    - https://iwatake2222.github.io/wasm_emscripten_test/main.html

# How to Build
It's just for build and test in local environment

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

or

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

# How to deploy
- See https://github.com/iwatake2222/wasm_emscripten_test/blob/master/.github/workflows/release_emscripten.yml
- Configure GitHub Pages in Settings -> Pages. Select gh-pages branch as Source
