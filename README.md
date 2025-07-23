# efficient_gmapping
针对空旷地带的高效gmapping手段

本改良版gmapping在针对雷达光线无法反射时的开阔地带建图情况作出了调整。当雷达无法反射时，默认射线起点处向外一段距离内为空旷地带。能够有效改善自主建图效率。

本方案还优化了三维点云压缩成二维点云，再转换成lasersacn类型数据时，点云过于稀疏导致雷达射线穿透障碍物的问题。当某条射线为inf时，检查左右n条射线。如果有不为inf的有效值，跳过该inf射线的处理。



## 运行方法

如果你已经下载了官方的gmapping包，先卸载它：

```
sudo apt-get remove ros-neotic-openslam-gmapping ros-neotic-gmapping
// 或者
sudo apt-get purge ros-neotic-openslam-gmapping ros-neotic-gmapping
```


然后把本功能包放到`{catkin_ws}\src\`下后到工作空间编译

跑优化版的gmapping的话运行下面的launch：

```
roslaunch gmapping slam_gmapping_pr2.launch
```


