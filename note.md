
debug configuartion for visual studio (right click on cmake target, add debug configuration)
```json
    {
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "gbemu.exe (gbemu\\gbemu.exe)",
      "name": "gbemu.exe (gbemu\\gbemu.exe)",
      "currentDir": "${workspaceRoot}",
      "args": [ "${workspaceRoot}\\roms\\01-special.gb" ]
    }
  ]
}

```

build:
```bash
# config - update the CMAKE_TOOLCHAIN_FILE to where your "vcpkg/scripts/buildsystems/vcpkg.cmake" are
# and set the VCPKG_TARGET_TRIPLET based on your machine, more on `vcpkg help triplet`
cmake -B build -S . -G Ninja -DCMAKE_BUILD_TYPE=Debug -DCMAKE_TOOLCHAIN_FILE="C:/Users/ethbr/local/bin/vcpkg/scripts/buildsystems/vcpkg.cmake" -DVCPKG_TARGET_TRIPLET=x64-windows

#build 
cmake --build build
```



