# floating_transform_publisher

This ROS package provides a simple publisher for "floating" TF transforms in URDF models. It is designed to simplify changing transforms and parent frames for objects that need to be adjusted for calibration purposes or need to be attached to a different parent frame such as a gripper.

The "floating_transform_publisher" reads the "robot_description" parameter and finds any "floating" joints, and publishes these transforms to /tf. The initial position of each floating transform is taken from the URDF joint origin description. The transforms can then be updated using the /update_floating_transform service, which takes a list of geometry_msgs/TransformStamped and updates the transforms. The "child_frame_id" must already exist in the list of transforms. No error checking is done to make sure the parent frame exists.

## Topics Published

### `tf`

The standard `/tf` topic with type `tf2_msgs/TFMessage`

## Services

### `/update_floating_transform

Takes a list of `geometry_msgs/TransformStamped` and updates the floating transforms. The "child_frame_id" must already exist in the list of transforms.

**Request**

* `geometry_msgs/TransformStamped[] transforms` - The updated transforms

**Response**

* `success` - True if the request was successful, otherwise false.

### `/reset_floating_transform

Reset all floating transforms to the URDF defaults.

**Request**

(empty)

**Response**

* `success` - True if the request was successful, otherwise false.



License: BSD