# **Figure.DIY** - Open-Source Household Chore Robot Demo

![Figure.DIY Project](assets/images/figure-diy-hero.jpg)

## Overview

**Figure.DIY** is a do-it-yourself replication of Figure AI's impressive household chore demo, using affordable open-source robotics. In the original demo, two humanoid robots (Figure 02 models) responded to simple voice commands and **collaboratively put away groceries by scanning their environment and adapting in real time**. Our goal is to recreate this scenario with low-cost components, showcasing that everyday chores can be automated without proprietary hardware. This aligns closely with the concept of **democratizing AI robotics for daily life**, by making advanced home automation **accessible and reproducible** to makers and researchers.

## Key Features

- **Voice-Commanded Task Execution**: Ability to understand and respond to natural language voice commands through **Whisper ASR**
- **Dual Robotic Arm Coordination**: Two **SO-ARM100** robotic arms working collaboratively to handle objects
- **Real-Time Object Detection**: Visual perception using **YOLOv8** to identify and locate objects in the environment
- **Neural Policy Control**: Trained imitation learning model for adaptive manipulation using the **LeRobot** framework
- **Edge AI Processing**: All computation performed locally on the **Jetson Orin NX** with no cloud dependencies

## Hardware Components

### Robotic Arms
- **Dual SO-ARM100 Robotic Arms**: Each arm provides **6 degrees of freedom** (6-DOF) using high-precision servos
- **Motors**: *Feetech STS3215 serial bus servos* with magnetic encoders (up to 19.5 kg·cm torque at 7.4V)
- **Control**: Dedicated motor control board per arm, interfacing via daisy-chained UART bus

### Computing Platform
- **reComputer J4012 (Jetson Orin NX 16GB)**: Central computing unit providing up to 100 TOPS of AI performance
- **Processing**: NVIDIA Ampere GPU (1024 CUDA cores and 32 Tensor cores), 6-core ARM CPU
- **Storage/Memory**: 16 GB RAM and 128 GB NVMe SSD preloaded with NVIDIA JetPack
- **I/O**: 4× USB 3.2 ports, HDMI output, Ethernet, and CSI camera interfaces
- **Power**: 20W-40W operating range with fan cooling

### Sensors & Perception
- **ReSpeaker Microphone Array**: USB-connected circular array with 4 digital microphones and built-in DSP
- **reCamera (Vision Camera)**: HD camera module for visual perception and object detection
- **Optional**: Additional cameras for multiple perspectives and improved depth perception

## Software Stack

- **Operating System**: NVIDIA JetPack (Ubuntu-based Linux) with AI libraries
- **Voice Recognition**: OpenAI's Whisper ASR in offline mode for speech transcription
- **Computer Vision**: YOLOv8 object detection model fine-tuned for household items
- **Robotics Framework**: LeRobot AI framework for imitation learning and policy deployment
- **Inter-Robot Communication**: Custom leader-follower orchestration for bimanual coordination

## Setup & Installation

### Prerequisites
- SO-ARM100 robotic arm kits (×2)
- Jetson Orin NX-based computer (reComputer J4012 recommended)
- ReSpeaker microphone array 
- HD camera compatible with the Jetson platform
- Workspace with stable mounting surface

### Hardware Assembly
1. Assemble both SO-ARM100 arms following the manufacturer's instructions
2. Mount arms securely on a stable base or table
3. Connect each arm's motor control board to the Jetson via USB
4. Position and connect the ReSpeaker and camera to the Jetson
5. Ensure proper power supply to all components

### Software Setup
1. Clone this repository: `git clone https://github.com/your-username/figure-diy.git`
2. Install dependencies: `cd figure-diy && pip install -r requirements.txt`
3. Download pre-trained models: `./scripts/download_models.sh`
4. Calibrate the system: `python calibrate.py`
5. Run the system: `python main.py`

## Usage

1. Power on the system and wait for initialization
2. Speak a command such as "Hey robot, put away the groceries"
3. The system will:
   - Acknowledge the command
   - Scan the environment to locate objects
   - Use Arm-A to pick up an object
   - Coordinate a handoff to Arm-B
   - Use Arm-B to place the object in the designated location
4. Repeat for additional objects or issue new commands

## Demos & Examples

- **Groceries Task**: Voice command "put away the groceries" triggers a sequence where the robot identifies, picks up, and stores various grocery items
- **Object Handoff**: Demonstrates robot-to-robot coordination with smooth object transfer between arms
- **Adaptive Grasping**: Shows the system adapting to different object shapes and sizes

## Future Enhancements

- Integration with mobile base for increased workspace
- Multi-modal sensing with tactile feedback
- Expanded vocabulary for more diverse task commands
- Learning from demonstration for new tasks without explicit programming

## Contributing

We welcome contributions to the **Figure.DIY** project! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to help with code, documentation, or hardware modifications.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Figure AI for the original inspiration
- The open-source robotics community for hardware designs and software tools
- NVIDIA for edge AI computing platforms that enable local processing
