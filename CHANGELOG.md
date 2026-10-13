# Changelog

## 2026-10-12

- **Works with any SangamIO robot, including the Roborock S5 Max.** The bridge
  no longer hard-codes CRL-200S constants. It converts wheel ticks and IMU
  counts with the `kinematics` group the robot publishes. Older SangamIO builds
  fall back to the CRL-200S (Proscenic M6 Pro) values.
- **Override any kinematics value with a ROS parameter:** `wheel_m_per_tick`,
  `wheel_track_m`, `wheel_tick_bits`, `gyro_rad_per_lsb`, `accel_mps2_per_lsb`
  (0 = use the robot's value). See "Robot Parameters" in the README.
- **CRL-200S gyro scale corrected** to 0.01025 °/s per count (was 0.061, about
  6x too high).
- `/imu` marks linear acceleration as not provided (covariance[0] = -1) when the
  robot advertises no accelerometer scale.
- `/scan` reports an inclusive `angle_max` (359°, not a duplicated 360°), by
  [@gkfabs](https://github.com/gkfabs).
- New dependency: `rcl_interfaces`.
