# a newer cmake is required to build
git clone https://github.com/Kitware/CMake.git
cd CMake/
./bootstrap && make
# result: bin/cmake

# chowmatrix
git clone https://github.com/Chowdhury-DSP/ChowMatrix.git
cd ChowMatrix/
git checkout v1.0.0
git submodule update --init --recursive
/compile/source/CMake/bin/cmake . -Bbuild
/compile/source/CMake/bin/cmake --build build --config Release
rm -rf /usr/local/lib/vst3/ChowMatrix.vst3
mkdir -p /usr/local/lib/vst3
cp -a build/ChowMatrix_artefacts/VST3/ChowMatrix.vst3 /usr/local/lib/vst3
cp -a build/ChowMatrix_artefacts/Standalone/ChowMatrix /usr/local/bin

tar czf /tmp/chowmatrix-1.0.0.x86_64.tar.gz /usr/local/lib/vst3/ChowMatrix.vst3
tar czf /tmp/chowmatrix-1.0.0.aarch64.tar.gz /usr/local/lib/vst3/ChowMatrix.vst3
tar czf /tmp/chowmatrix-1.0.0.armv7l.tar.gz /usr/local/lib/vst3/ChowMatrix.vst3

# chowtapemodel
apt-get install libasound2-dev libxcursor-dev libxinerama-dev libxrandr-dev freeglut3-dev libjack-jackd2-dev libcurl4-openssl-dev
git clone https://github.com/jatinchowdhury18/AnalogTapeModel.git
cd AnalogTapeModel
git checkout v2.7.0
git submodule update --init --recursive
cd Plugin/ && bash build_linux.sh
rm -rf /usr/local/lib/vst3/CHOWTapeModel.vst3
mkdir -p /usr/local/lib/vst3
cp -a Builds/LinuxMakefile/build/CHOWTapeModel.vst3 /usr/local/lib/vst3
mkdir -p /usr/local/lib/vst
cp -a Builds/LinuxMakefile/build/CHOWTapeModel.so /usr/local/lib/vst
rm -rf /usr/local/lib/lv2/CHOWTapeModel.lv2
mkdir -p /usr/local/lib/lv2
cp -a Builds/LinuxMakefile/build/CHOWTapeModel.lv2 /usr/local/lib/lv2
rm -f /usr/local/bin/CHOWTapeModel
cp -a Builds/LinuxMakefile/build/CHOWTapeModel /usr/local/bin

tar czf /tmp/CHOWTapeModel-2.7.0.x86_64.tar.gz /usr/local/lib/vst3/CHOWTapeModel.vst3 /usr/local/lib/vst/CHOWTapeModel.so /usr/local/lib/lv2/CHOWTapeModel.lv2 /usr/local/bin/CHOWTapeModel
tar czf /tmp/CHOWTapeModel-2.7.0.aarch64.tar.gz /usr/local/lib/vst3/CHOWTapeModel.vst3 /usr/local/lib/vst/CHOWTapeModel.so /usr/local/lib/lv2/CHOWTapeModel.lv2 /usr/local/bin/CHOWTapeModel
tar czf /tmp/CHOWTapeModel-2.7.0.armv7l.tar.gz /usr/local/lib/vst3/CHOWTapeModel.vst3 /usr/local/lib/vst/CHOWTapeModel.so /usr/local/lib/lv2/CHOWTapeModel.lv2 /usr/local/bin/CHOWTapeModel
