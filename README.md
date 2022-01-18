## 多激光雷达外参自动标定（ROS）
#### 了解详细算法和代码细节，以及获取测试数据实践，见博客：https://adamshan.blog.csdn.net/article/details/105930565 或 https://www.bilibili.com/read/cv10769496

由于livox的FOV不是360度，如果标定结果不收敛，需要尝试调整初始的位置和姿态的数值

标定运行状态视频可查看 https://www.bilibili.com/video/BV1fb4y1J7iw/

资源来源于网络，稍作调整，可以一次标定一组两个livox的激光雷达，需要在空旷的场地录制rosbag，得出的tf数据可以辅助在livox_viewer里手动调整外参的数值

问题：

1. 默认livox激光雷达的frame_id都是livox_frame，代码里只是在第107行把待标定激光雷达的frame_id在程序里有调整成livox_child，但rosbag中待标定激光雷达的frame_id还是livox_frame
2. 基于第1点原因，运行tf.launch并不能生效
