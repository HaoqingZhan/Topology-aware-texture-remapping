# Topology-aware texture remapping
TPPack is a new framework for texture remapping of Photogrammetric 3D Building Models. It can be used to solve the problems of severe structural fragmentation, poor topological continuity and low space utilization of the input model texture. 
<img width="5294" height="2027" alt="image" src="https://github.com/HaoqingZhan/Topology-aware-texture-remapping/blob/main/docs/images/1.jpg" />


## 1 Core Features
### 1.1 Structure-preserving adaptive parameterization
- For the input mesh, the method first performs a parameterization-oriented surface structural segmentation and conducts an initial parameterization on the resulting charts. The charts are then adaptively re-segmented based on locations where the parameterization fails, and each resulting sub-chart is reparameterized individually. Finally, the sub-charts are merged back into the original charts to complete the structure-preserving chart parameterization.
<img width="7325" height="1839" alt="image" src="https://github.com/HaoqingZhan/Topology-aware-texture-remapping/blob/main/docs/images/2.jpg" />

### 1.2 Chart alignment and combination
- After obtaining structure-preserving parameterizations, the alignment between atlas is carried out to maintain the continuity of texture space and improve the utilization of atlas. This process makes full use of the three-dimensional topological adjacency between charts, and realizes the close alignment between chart boundaries through accurate parameter domain transformation in the unified reference system.
<img width="5180" height="2095" alt="image" src="https://github.com/HaoqingZhan/Topology-aware-texture-remapping/blob/main/docs/images/3.jpg" />


## 2 Usage
### 2.1 Parameter Description
<img width="874" height="528" alt="image" src="https://github.com/HaoqingZhan/Topology-aware-texture-remapping/blob/main/docs/images/4.png" width="400" />

| Parameter | Description |
|-----------|-------------|
| `Input OBJ` | Input 3D model path (.obj format) |
| `Output Name` | Output obj name (The output directory is the same as the directory where the exe file is located) |
| `N Value` | The difference in normal angles of charts for alignment and combination (Not required by default. If set, its range should be 0-15) |
| `Accuracy Mode` | Sets the precision of the output texture (Not required by default, or you can set the precision by res(resolution), tpu(Texels-per-unit) or origin(Maintain the tpu of the input texture)) |
| `Value` | If the precision is set by res or tpu, fill in the target resolution or Texels-per-unit value (fill in int for res or float for tpu) |

### 2.2 Example
- Process the model in default.
<img width="877" height="528" alt="image" src="https://github.com/HaoqingZhan/Topology-aware-texture-remapping/blob/main/docs/images/5.png" width="400" />
<img width="2705" height="1568" alt="image" src="https://github.com/HaoqingZhan/Topology-aware-texture-remapping/blob/main/docs/images/6.jpg" />


## 3 Some results
### 3.1 Structure-preserving adaptive parameterization
<img width="9229" height="9714" alt="image" src="https://github.com/HaoqingZhan/Topology-aware-texture-remapping/blob/main/docs/images/7.jpg" />

### 3.2 Chart alignment and combination
<img width="5192" height="9108" alt="image" src="https://github.com/HaoqingZhan/Topology-aware-texture-remapping/blob/main/docs/images/8.jpg" />

### 3.3 Two-step comparison
<img width="8005" height="13833" alt="image" src="https://github.com/HaoqingZhan/Topology-aware-texture-remapping/blob/main/docs/images/9.jpg" />


## 4 Application Scenarios
- It is mainly used for 3D models with obvious topological characteristics of buildings and other structures;
- Digital Twin/Smart City: Reduce resource usage of models in large-scale scenes and optimize rendering efficiency;
- 3D Visualization Toolchain: Integrate into automated pipelines to batch process model optimization;
- The application of topological continuity of texture atlas is still to be developed.


## 5 Notes
1. Only .obj format 3D models are supported currently;
2. If the resolution or the Texels-per-unit (TPU) is set too large, it will take longer to run;
3. The topological characteristics of different models are different. Choosing an appropriate value of n can get better results, and if n is unreasonable, it will lead to wrong results;
<img width="5481" height="3018" alt="image" src="https://github.com/HaoqingZhan/Topology-aware-texture-remapping/blob/main/docs/images/10.jpg" />
4. At present, the framework uses the modified MaxRects-BL algorithm to pack charts and chart combinations. We will introduce more advanced packing algorithms in the future.


## 6 Contribution
Welcome to submit Issues to report problems, propose feature suggestions, or participate in code optimization via Pull Requests.


## 7 License
This project is open source under the [MIT License](LICENSE), free to use, modify and distribute.

