# Las2Mesh

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

A tool to convert point cloud (.las format) files into 3D models. The output formats supported are .ply, .stl, .obj, .off, .gltf, and .glb.

## Download

- [v0.2](https://github.com/ksasao/Las2Mesh/releases/download/v0.2/las2mesh_v0.2.zip) (2022/04/11)
- [Previous Versions](https://github.com/ksasao/Las2Mesh/releases)

## Usage

Drag and drop the point cloud (.las) file(s) onto las2mesh.exe. Multiple files can be dropped together to output a single 3D model. The default file name is output.ply. The output format is automatically determined by the file extension specified in the -o option. The output will have vertex colors.

![Izu-kyū Shimoda Station area (-d 11 option)](material/izukyushimoda_d11.png)
Created using the .las file from [G-Spatial Information Center, Shizuoka, Mount Fuji Southeast - Izu East, Point Cloud Data LPData](https://www.geospatial.jp/ckan/dataset/shizuoka-2019-pointcloud/resource/d5e98a7b-f15c-45b0-bf40-0287f5b1de68) (License: [Creative Commons Attribution](http://opendefinition.org/licenses/cc-by/))

### Options

```txt
Las2Mesh v0.2
usage: las2mesh.py [-h] [-d DEPTH] [-o OUTPUT] [-n] [files ...]

Generate a mesh from .las files

positional arguments:
  files                 .las files to process. Can specify multiple.

optional arguments:
  -h, --help            show this help message and exit
  -d DEPTH, --depth DEPTH
                        Specify mesh detail as an integer. Default is 10.
  -o OUTPUT, --output OUTPUT
                        Specify output file name. Default is output.ply. Supports .ply, .stl, .obj, .off, .gltf.
  -n, --nopreview       Disable 3D preview
```

## M1 Mac Setup

Install Python:
```
brew install python
```

Make python command available:
```
sudo ln -s /opt/homebrew/bin/python3 /opt/homebrew/bin/python
```

Build [Open3D](https://github.com/isl-org/Open3D) ([see also](http://www.open3d.org/docs/release/compilation.html)):
```
git clone https://github.com/isl-org/Open3D
cd Open3D
mkdir build
cd build
cmake ..
make -j$(sysctl -n hw.physicalcpu)
sudo make install
make install-pip-package
make python-package
make pip-package
```

Install Python libraries:
```
pip3 install numpy laspy pygltflib
```

Test conversion (after cloning Las2Mesh):
```
cd src
python las2mesh.py test.las -o test.glb
```

## License

Apache License 2.0