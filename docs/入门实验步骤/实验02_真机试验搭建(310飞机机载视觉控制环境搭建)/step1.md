# 实验02_真机试验搭建（310飞机机载视觉控制环境搭建）

## 1. 实验背景

对于一个 310 旋翼无人机而言，为了完成各类视觉任务（如定位建图、目标检测等），最基本的要求是无人机具备高度稳定性，并且其各项性能应与任务需求相匹配。为了便于学习、实验与研究，以下介绍该型号无人机的调试与检修方法。

通过对 310 无人机进行系统调试与定期检修，可以确保其飞行系统的安全性与可靠性，有效预防飞行事故的发生，这对于保障人员生命安全至关重要。同时，实际操作也有助于提升调试与维护技能，并深化对航空系统理论的理解。在进行相关实验前，确保无人机性能稳定，能够进一步提高实验结果的准确性及数据的可靠性。

## 2. 环境准备

<table><tr><td rowspan="2">序号</td><td rowspan="2">软件环境</td><td colspan="2">硬件环境</td></tr><tr><td>名称</td><td>数量(个)</td></tr><tr><td>1</td><td>Windows 10 及以上版本</td><td>笔记本/台式电脑①</td><td>1</td></tr><tr><td>2</td><td>RflySim 工具链</td><td>310 飞机以及配套设备</td><td>1</td></tr><tr><td>3</td><td>Nomachine 软件</td><td>飞思障碍物</td><td>2</td></tr><tr><td>4</td><td></td><td>飞机圆环和方框</td><td>若干</td></tr><tr><td>5</td><td></td><td>USB 数据线</td><td>若干</td></tr></table>


推荐配置请见： https://rflysim.com/doc/zh/1/InstallLearn.html


## 3. 飞机检查

### 步骤一：遥控器对码

#### 1.对码

长按遥控器电源键开机，进入到遥控器的主界面，之后点击遥控器界面上的“WFLY”的图标，即可进入到遥控器的设置界面中去。设置界面中有四个选项，我们需要点击“通信设置”，之后点击“对码”选项，找到对码后的“开始”选项。点击“开始”后，我们需要通过数据线对310无人机进行供电，等待遥控器界面显示对码完成即可。

![image](pics/step1_pics/1.jpeg)


![image](pics/step1_pics/2.jpeg)


![image](pics/step1_pics/3.jpeg)


![image](pics/step1_pics/4.jpeg)



<center>图 1 遥控器对码步骤图</center>



当遥控器发出“滴”的提示音后，并出现下图所示，说明对码完成。注：如出现对码失败，请重新对码并插拔与飞机连接的数据线即可。

![image](pics/step1_pics/5.jpeg)



<center>图 2 对码完成</center>


### **步骤二：传感器校准**

使用数据线Type-C 端连接 310 飞机飞控 Type-C 端口如图 3 所示，USB 端连接本地电脑，打开QGC可以看到连接成功。

![image](pics/step1_pics/6.jpeg)



<center>图 3 连接飞控</center>


#### 1.罗盘校准。

点击Vehicle Setup 中传感器，再次点击罗盘，如图所示在弹出的窗口点击OK，依次按照图示的角度方向摆放飞机，对应的飞机图会变成黄色，接着按照图示连续旋转飞机，直至标记为已完成，已完成时颜色会变绿。重复以上步骤多次，知道每个方向角度都校准完毕，此时会弹出窗口显示罗盘校准完成。

![image](pics/step1_pics/7.png)



<center>图 4 罗盘校准</center>


![image](pics/step1_pics/8.jpeg)



<center>图 5 校准罗盘完毕</center>


#### 2. 陀螺仪校准

点击陀螺仪，会弹出校准陀螺仪的窗口，点击OK，然后将飞机静置，3s后陀螺仪校准完毕。

![image](pics/step1_pics/9.png)



<center>图 6 陀螺仪校准</center>


![image](pics/step1_pics/10.jpeg)



<center>图 7 陀螺仪校准完毕</center>


#### 3 加速度计校准

点击加速度计，此时会弹出窗口提示校准角速度计，点击OK 后，依次按照图示摆放飞机，校准完成后对应的飞机姿态会变绿，重复步骤直至所有飞机角度方向变绿。

![image](pics/step1_pics/11.jpeg)



<center>图 8 校准加速度计完毕</center>




#### 4. 校平地平线（重要 刚开始手飞这个不校准的话飞机会寻找错误的地平线导致乱飞）

将飞机至于平面，点击校平地平线，在弹出的窗口点击OK 既可完成校准地平线。

![image](pics/step1_pics/12.png)



<center>图 9 校准地平线</center>




### **步骤三：遥控器校准（一定要好好看）**

点击QGC左上方后点击 Vehicle Setup，接着点击 Radio（遥控器），点击校准，接着点击OK，点击下一步，按照右上角提示进行遥控器的校准。

![image](pics/step1_pics/13.jpeg)



<center>图 10 开始校准遥控器</center>




![image](pics/step1_pics/14.png)


![image](pics/step1_pics/15.png)



<center>图 11 校准遥控器</center>




### **步骤四：遥控器飞行模式与通道设置**

1.Kill 键设置。点击 QGC 右上角后选择 Vehicle Setup 后选择飞行模式界面，点击Emergency Kill Switch channel 右边的通道设置，下拉选择 Channel 6 作为 kill 键的控制键，也即SA键。

![image](pics/step1_pics/16.jpeg)



<center>图 1 2  kill  键的选择</center>



2.飞行模式键的设置。点击模式频道右边的通道设置，下拉选择Channel 5作为飞行模式键的控制键，也即 SB键。

![image](pics/step1_pics/17.jpeg)



<center>图 13 飞行模式键的设置</center>



3.Arm 键的设置。点击 Arm switch channel 右边的通道设置，下拉选择 Channel 8 作为arm键的控制键，也即 SC键。

![image](pics/step1_pics/18.jpeg)



<center>图 14 arm 键的设置</center>



4.Offboard 键的设置。点击 Offboard switch channel 右边的通道设置，下拉选择 Channel7 作为arm键的控制键，也即 SC键。

![image](pics/step1_pics/19.jpeg)



<center>图 15 Offboard 键的设置</center>




### **步骤五：飞控参数设置**

点击QGC左上方后点击 Vehicle Setup，接着点击参数进入参数设置界面，为了确保能够进行视觉或者激光的导航定位，设置 EKF2_AID_MASK （导航融合算法）为 第四项vision position fusion 和 第五项 vision yaw fusion，设置 EKF2_HGT_MODE（确定 EKF 使用的高度数据的主要来源）为 第四项 Vision 。

![image](pics/step1_pics/20.jpeg)



<center>图 16 设置 EKF2_AID_MASK</center>




![image](pics/step1_pics/21.jpeg)



<center>图 17 设置 EKF2_HGT_MODE</center>




### **步骤六：nomachine 连接和 PX4 文件配置**

1.在笔记本电脑端打开 nomachine进入连接页面，点击左上角add按钮进入编辑连接界面

![image](pics/step1_pics/22.png)



<center>图 18 nomachine 连接页面图</center>



2.在Host处输入飞机 ip地址，点击右上角 add后回到连接页面，如图 19所示。飞机ip可以用显示屏连接飞机后在终端输入命令得到，也可使用路由器的后台管理得到。

![image](pics/step1_pics/23.png)



<center>图 19 nomachine 编辑连接页面图</center>



3.双击要连接的飞机 ip后进入账号密码界面，输入账号 nvidia和密码 nvidia后点击OK后一直点击OK如图 21所示，即可进入飞机远程既可进入NX远程界面。

![image](pics/step1_pics/24.png)



<center>图 20 双击 nomachine 的 IP 地址连接飞机</center>



![image](pics/step1_pics/25.png)



<center>图 21 输入账号密码</center>




4. 在 windows 电脑上，在搜索栏输入 CMD，点击打开一个终端，终端中输入 ipconfig，查看 windows 电脑 IP。

![image](pics/step1_pics/26.png)



<center>图 22 查看 ip</center>



5.进入飞机远程，在任意位置打开一个终端，输入 `roscd mavros/launch/` 后按下回车键，接着输入 `sudo gedit px4.launch` 后输入密码 nvidia，接着会打开一个 px4.launch 文件。

![image](pics/step1_pics/27.png)



<center>图 23 打开 px4.launch 文件</center>



6.在 default="udp://@这一行的 ip 地址修改为 windows 电脑 ip 地址后保存文件。ip 地址后的15502是310飞机默认的连接QGC端口号。

![image](pics/step1_pics/28.jpeg)



<center>图 24 编辑 px4.launch</center>




### **步骤七：QGC 连接**

点击QGC左上方选择应用设置，选择通信连接，点击下方add后，在name处输入15502，type 处选择UDP，Port处输入15502，保存即可。

![image](pics/step1_pics/29.jpeg)



<center>图 25 QGC 连接设置</center>




### **步骤八：各个传感器的启动**

#### 1.单个传感器启动

1.310 飞机传感器包括前视相机（D435i）、下视相机（单目）、激光雷达、px4。在任意终端内输入 `roslaunch realsense2_camera rs_camera.launch`

![image](pics/step1_pics/30.jpeg)



<center>图 26 打开前视相机</center>



2.打开一个终端， 输入 `rostopic echo /camera/color/image_raw` 后回车有数据输出表示前视相机已经开启。 另开一个终端 ，输入 rviz，接着再选择图像话题 /camera/color/image_raw 中

的image，如果左下角出现图像，表明相机正常开启，如果是纯黑图像，表明相机未正常开启如图 28所示。

![image](pics/step1_pics/31.jpeg)


![image](pics/step1_pics/32.jpeg)



<center>图 27 查看前视相机数据</center>




![image](pics/step1_pics/33.jpeg)



<center>图 28 前视相机开启</center>



3.在终端输入 `roslaunch usb_cam usb_cam-test.launch` 可以打开下视单目相机

![image](pics/step1_pics/34.jpeg)



<center>图 29 打开下视相机</center>



4.打开一个终端， 输入 `rostopic echo /usb_cam/image_raw` 后回车有数据输出表示下视相机正常开启。另开一个终端， 输入 rviz，接着再选择图像话题 /camera/color/image_raw 中的image，如果左下角出现图像，表明相机正常开启，如果是纯黑图像，表明相机未正常开启如图 31所示。

![image](pics/step1_pics/35.jpeg)


![image](pics/step1_pics/36.jpeg)



<center>图 30 查看下视相机数据</center>




![image](pics/step1_pics/37.jpeg)



<center>图 31 查看下视相机图像</center>



5.输入 `roslaunch livox_ros_driver2 rviz_MID360.launch` 可以打开激光雷达，同时也会打开一个 rviz 显示激光雷达扫描的点云。

![image](pics/step1_pics/38.jpeg)



<center>图 32 打开激光雷达</center>



6.打开一个终端， 输入 `rostopic echo /livox/lidar` 后回车有数据输出表示激光正常开启。

![image](pics/step1_pics/39.jpeg)


![image](pics/step1_pics/40.jpeg)



<center>图 33 查看激光雷达输出</center>




如果rviz中的激光点云与环境相似，那么代表激光雷达也正常运行且数据也正常。

![image](pics/step1_pics/41.jpeg)



<center>图 34 激光点云</center>



7.输入 `echo nvidia | sudo -S chmod 777 /dev/ttyTHS0 && roslaunch mavros px4.launch` 可以打开 px4.打开一个终端， 输入 `rostopic echo /mavros/state` 有数据持续输出且 connected 为True 表示 px4（mavros）正常开启。

![image](pics/step1_pics/42.jpeg)



<center>图 35 打开 mavros（px4）</center>




![image](pics/step1_pics/43.jpeg)



<center>图 36 查看 mavros 状态</center>




#### 2.多个传感器启动检查

1.关闭之前打开的传感器终端，在/home/nvidia/Downloads/takeoff_test 文件夹下的空白处点击鼠标右键，打开一个终端，输入命令./sensor.sh 会依次打开前视相机，下视相机，激光雷达，mavros。在启动传感器之后，会自动检查传感器是否正常开启，如果正常开启会显示对应的图像和点云信息，同时会加载一个小窗口，小窗口显示对应的图像以及话题信息为OK 如图 37所示。

![image](pics/step1_pics/44.jpeg)



<center>图 37 传感器正常开启</center>




2.假设激光雷达未正常开启，下视相机未正常开启，那么 rviz中的点云是空的，下视相机图像不会加载出来，同时在窗口中会提示“xx 话题接收空数据，请查看XX是否正常开启”的信息如所示。

![image](pics/step1_pics/45.jpeg)



<center>图 38 激光雷达与下视相机未正常开启</center>




### 步骤九：起飞检查

1. 在完成各种配置后，需要进行实飞检查，确保无人机能够完成实飞操作。进入/home/nvidia/Downloads/takeoff_test/takeoff 文件夹内，打开终端后输入命令./start.sh 后运行start.sh 开启激光雷达，px4 和激光定位模块，同时开启自动起飞与降落脚本 check_fly.py如图 39所示。


![image](pics/step1_pics/46.jpeg)



<center>图 39 自动起飞降落程序</center>




2.在所有程序都开启后，首先会进行 遥控器、电池、遥控器 SA 键（kill 键）的校验，此时会打开一个窗口，窗口内显示校验的内容如图 40 所示，校验成功后方可进行下一步。

![image](pics/step1_pics/47.jpeg))



<center>图 40 校验电池和遥控器</center>



3.在完成电池校验后，需要开始定位数据和飞行模式的校验。如果定位精度过低，那么会额外弹出一个窗口，窗口内提示“显示定位精度过低，请重新定位，3s后关闭程序”如所示，此时需要关闭校验步骤的窗口退出程序，并重新查看是否正常开启激光雷达以及激光定位模块。

!![image](pics/step1_pics/48.jpeg)



<center>图 41 定位精度过低</center>



4.如果定位精度没有问题，那么就会开始飞行模式校验。当前飞机如果不是定点模式，那么会加载一个 gui 界面提示 “当前为定高模式，请切换定点模式！将 SB 键拨到最下方，飞行模式切换为定点模式”。

![image](pics/step1_pics/49.jpeg)



<center>图 42 切换定点模式提示</center>




5.如果当前飞机已经切换到定点模式，那么会弹出 “满足实飞条件！窗口即将关闭。窗口关闭后，将 SA 键拨动到最下边， 遥控器 SD 键拨到最上方，接着将 SC 键拨到最下方进入 Offboard。

![image](pics/step1_pics/50.jpeg)



<center>图 43 满足实飞条件</center>



6.将 SA 键拨动到最下边，遥控器 SD 键拨到最上方，接着将 SC 键拨到最下方进入Offboard，操作如图 44 所示。当进入 offboard 模式起飞后左右手可以无需进行操作。 注：如果在飞行过程中飞机乱飞，见问题7。

![image](pics/step1_pics/51.jpeg)



<center>图 44 实飞操作</center>



7.进入offboard 模式后，无人机会起飞到 0.8m后悬停2s， 并加载一个提示窗口如图所示。

![image](pics/step1_pics/52.jpeg)



<center>图 45 到达目标位置</center>




8.到达目标位置后飞机会开始降落， 降落期间会加载窗口如图 46所示。

![image](pics/step1_pics/53.jpeg)



<center>图 46 准备降落</center>



9.当无人机降落到地面后会自动进行落地检测 检测到无人机降落到地面后会加载窗口如图 47所示。

![image](pics/step1_pics/54.jpeg)



<center>图 47 降落成功</center>



10.飞机降落的提示窗口关闭后，将遥控器 SA 键往最下方拨动，将 SD 键拨到最上方，最后将遥控器 SC 键拨到最上方，如图 48 所示。同时可以看到起飞检查环节完成了如下步骤如图 49所示。

![image](pics/step1_pics/55.jpeg)



<center>图 48 飞机落地操作步骤</center>




![image](pics/step1_pics/56.jpeg)



<center>图 49 完成步骤</center>




完成了以上步骤表明飞机 可以进行的定位飞行，Offboard 程序控制飞行。

## 4.常见问题

Q1: 使用数据线连接电脑和飞控后，QGC 显示 Communication Lost 怎么办？

A1: 这是因为上一次 QGC 连接飞控断开后没有关闭 GQC，此时只需要点击断开连接按钮后即可再次连接。

Q2: D435I相机无法正常运行怎么办？

A2: 拔下310飞机的电源，重新上电即可

Q3: 下视相机无法正常启动怎么办？

A3: 拔下310飞机的电源，重新上电即可

Q4: PX4 无法正常启动怎么办？

A4: 重新插拔连接飞控的 usb 线再次启动 px4。

Q5： 如果更换了飞控，如何重新烧录固件和参数

A5： 双击打开"/桌面/RflyTools/ QGroundControl"进入 QGC，点击软件左上角图标，然后点击“Vehicle Setup”如图 50所示，在“固件”界面使用USB数据线连接主机与310飞机，等待“固件设置”界面弹出后，按图 51 所示选择“自定义固件”，点击“OK”即可选择自定义固件。如果选择官方固件，则根据自己的需求选择不同的固件如图 52所示。

![image](pics/step1_pics/57.png)



<center>图 50 进入 QGC</center>




![image](pics/step1_pics/58.jpeg)



<center>图 51 自定义固件</center>




![image](pics/step1_pics/59.jpeg)



<center>图 52 刷入官方固件</center>




固件烧录完成后等待飞控重新启动并自动连接 QGC（若没有自动连接请重新插拔连接飞控端的 USB 数据线），然后选择“Vehicle Setup Parameters Tools→Load from file…”

![image](pics/step1_pics/60.jpeg)



<center>图 53 选择参数</center>




在弹出的“选择参数文件”窗口中，打开本节实验目录，选择参数文件（参数文件以实际给出的参数为实际标准），点击“打开”，点击确定既可开始刷入参数，等待烧录完成。参数烧录完成后，需要重新启动给飞控上电，或者在飞控中重启飞控。

![image](pics/step1_pics/61.jpeg)v



<center>图 54 刷入参数</center>




![image](pics/step1_pics/62.jpeg)



<center>图 55 刷入参数</center>




![image](pics/step1_pics/63.jpeg)



<center>图 56 重启飞行器，参数生效</center>


Q6: 镜像损坏了如何还原？

A6: 首先将 310 飞机的硬盘拆下来，将 310 飞机的 SSD 固态硬盘（图片中硬盘作为参考，以实际的硬盘为准）取出后，插入硬盘读取器中并连接到电脑，设备连接图如下：

![image](pics/step1_pics/64.jpeg)


接下来打开DiskGenius硬盘分区软件（如果未下载，需要下载）。选择菜单栏中的“磁盘->从镜像文件还原磁盘”。

![image](pics/step1_pics/65.jpeg)


![image](pics/step1_pics/66.jpeg)


选择下载本地的.pmfx 格式镜像的文件（以我们给出的镜像为准），选择打开。

![image](pics/step1_pics/67.png)


确认选择的镜像文件与目标磁盘是否选择正确，恢复模式选择所有扇区点击开始。注：此处一定要确认选择的为插入电脑中的 SSD 盘，避免选择错误造成数据损坏。

![image](pics/step1_pics/68.jpeg)


需要等待20-30分钟，等待镜像拷贝完成即可。

![image](pics/step1_pics/69.jpeg)


完成后，将SSD装回310飞机中即可。

Q7：如果无人机在测试程序控制时乱飞怎么办？

A7：拨动遥控器 SC 摇杆切出 Offboard 模式，缓慢拨下左摇杆让无人机降落，降落后将遥控器摇杆 SD 拨到最下方，摇杆 SA（kill 键）拨到最上方如错误!未找到引用源。所示，将打开的终端全部关闭即可

![image](pics/step1_pics/70.png)