# rosbridge
Bridge from Gym to ROS robots




## Fetch high level
 * See [Docs](http://docs.fetchrobotics.com/), especially the [API](http://docs.fetchrobotics.com/api_overview.html)

### Action and observation space
 * Observation is a tuple of
   - joint angles [Nj x 1]
   - kinematic coordinates [Nb x 12]
   - measured joint torques [Nj x 1]
   - lidar scan [Ns x 1]
   - camera [Nh x Nv]
 * Action is a vector of
   - joint target positions [Nj x 1]
   - forward velocity [1]
   - rotational velocity [1]
   - (other action spaces might be added)

### Ros Topics
  * Subscribe to `head_camera/depth_registered/points`, of type   [sensor_msgs/PointCloud2](http://docs.ros.org/api/sensor_msgs/html/msg/PointCloud2.html)
  * Subscribe to `base_scan` of type [sensor_msgs/LaserScan](http://docs.ros.org/api/sensor_msgs/html/msg/LaserScan.html)
  * Subscribe to `imu` of type [sensor_msgs/Imu](http://docs.ros.org/api/sensor_msgs/html/msg/Imu.html)

  * Write to `arm_with_torso_controller/follow_joint_trajectory` of type [control_msgs/FollowJointTrajectory](http://docs.ros.org/api/control_msgs/html/action/FollowJointTrajectory.html)
    - Or maybe a higher level interface through Moveit.
  * Write to `cmd_vel` of type [geometry_msgs/Twist](http://docs.ros.org/api/geometry_msgs/html/msg/Twist.html)
  * Write to `head_controller/point_head` of type [control_msgs/PointHead](http://docs.ros.org/api/control_msgs/html/action/PointHead.html)
  * Write to `gripper_controller/gripper_action` of type [control_msgs/GripperCommand](http://docs.ros.org/api/control_msgs/html/action/GripperCommand.html)
    - turn a single grip strength number into position and effort, where <=0 means open and >0 means closed with corresponding effort

## Fetch low level
