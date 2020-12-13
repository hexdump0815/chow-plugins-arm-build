# a newer cmake is required to build
git clone https://github.com/Kitware/CMake.git
cd CMake/
./bootstrap && make
# result: bin/cmake

# chowmatrix
git clone https://github.com/Chowdhury-DSP/ChowMatrix.git
cd ChowMatrix/
git submodule update --init --recursive
/compile/source/CMake/bin/cmake . -Bbuild
/compile/source/CMake/bin/cmake --build build --config Release
rm -rf /usr/local/lib/vst3/ChowMatrix.vst3
mkdir -p /usr/local/lib/vst3
cp -a build/ChowMatrix_artefacts/VST3/ChowMatrix.vst3 /usr/local/lib/vst3

tar czf /tmp/chowmatrix-1.0.0.x86_64.tar.gz /usr/local/lib/vst3/ChowMatrix.vst3
tar czf /tmp/chowmatrix-1.0.0.aarch64.tar.gz /usr/local/lib/vst3/ChowMatrix.vst3
tar czf /tmp/chowmatrix-1.0.0.armv7l.tar.gz /usr/local/lib/vst3/ChowMatrix.vst3
