# ROS
# 建议 640x480@30，先开对齐、同步和点云
ros2 launch realsense2_camera rs_launch.py \
  enable_rgbd:=true enable_sync:=true align_depth.enable:=true \
  pointcloud.enable:=true \
  depth_module.profile:=640x480x30 rgb_camera.profile:=640x480x30
ros2 launch rtabmap_launch rtabmap.launch.py \
  rtabmap_args:="--delete_db_on_start" \
  rgb_topic:=/camera/camera/color/image_raw \
  depth_topic:=/camera/camera/depth/image_rect_raw \
  camera_info_topic:=/camera/camera/color/camera_info \
  frame_id:=camera_link \
  approx_sync:=true qos:=2 rviz:=true
