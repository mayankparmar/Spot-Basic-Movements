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