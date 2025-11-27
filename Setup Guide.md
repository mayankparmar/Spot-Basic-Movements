# Instructions to Setup Development Environment for Spot on NVIDIA Jetson Orin Nano Super


## Prerequisites

- Ubuntu 22.04 LTS (recommended)
- Python 3.8+
- CUDA-capable GPU (for Isaac Sim)
- Jetson Xavier NX or similar (for hardware deployment)

---

## 0. Update Ubuntu and Check Versions
 1. Update OS
    ```bash
    sudo apt update
    ```
    ```bash
    sudo apt upgrade
    ```
 2. Confirm GCC and G++ are at the least version 11.
    ```gcc --version```
    ```g++ --version```
3. Check NVIDIA driver version (525 or later)
    ```nvidia-sim```

## 1. Isaac Sim Installation
1. Clone Isaac Sim from NVIDIA's Git:
   ```bash
   git clone https://github.com/isaac-sim/IsaacSim.git isaacsim
   ```
   ```bash
   cd isaacsim
   ```
2. Build IsaacSim
   ```bash
   ./build.sh
   ```
3. Test Run IsaacSim
   ```
   cd _build/linux-aarch64/release
   ```
   ```
   ./isaac-sim.sh
   ```

## 2. Install ROS 2 and ROS Bridge
1. Add _Universe_ repository.
   ```bash
   sudo apt install software-properties-common
   ```
   ```bash
   sudo add-apt-repository universe
   ```

2. Install ROS2-apt-source
   ```bash
   sudo apt update && sudo apt install curl -y
   ```
   ```bash
   export ROS_APT_SOURCE_VERSION=$(curl -s https://api.github.com/repos/ros-infrastructure/ros-apt-source/releases/latest | grep -F "tag_name" | awk -F\" '{print $4}')
   ```
   ```bash
   curl -L -o /tmp/ros2-apt-source.deb "https://github.com/ros-infrastructure/ros-apt-source/releases/download/${ROS_APT_SOURCE_VERSION}/ros2-apt-source_${ROS_APT_SOURCE_VERSION}.$(. /etc/os-release && echo ${UBUNTU_CODENAME:-${VERSION_CODENAME}})_all.deb"
   ```
   ```bash
   sudo dpkg -i /tmp/ros2-apt-source.deb
   ```

3. Install ROS 2 packages
   ```bash
   sudo apt update
   ```
   ```bash
   sudo apt upgrade
   ```
   ```bash
   sudo apt install ros-humble-desktop
   ```
   ```bash
   sudo apt install ros-dev-tools
   ```

4. Setup Environment Variables
   ```bash
   source /opt/ros/humble/setup.bash
   ```