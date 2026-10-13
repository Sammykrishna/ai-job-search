# Candidate Profile

## Identity
- **Name:** Samanth Krishna
- **Location:** Garten Strasse 41, 88250 Weingarten, Germany
- **Phone:** (+49) 155 6078 3621
- **Email:** samanthkrishna2001@gmail.com
- **LinkedIn:** linkedin.com/in/samanth-krishna-429126202
- **GitHub:** github.com/Sammykrishna
- **Languages:** English (C1 - Fluent), German (A2 - Basic), Telugu (Native), Tamil (Fluent), Hindi (Basic)
- **Status:** M.Sc. Mechatronics student (RWU, 4th semester, ongoing), seeking internship or Werkstudent roles in robotics and physical AI
- **Constraints:** None - open to relocating anywhere in Germany or broader Europe, and open to on-site, remote, or hybrid

## Education

| Degree | Period | Institution | Key Topics |
|--------|--------|-------------|------------|
| M.Sc. Mechatronics (4th semester, ongoing) | 10/2024-present | Ravensburg-Weingarten University of Applied Sciences (RWU), Germany | Robotics, computer vision, autonomous systems |
| B.Tech. Robotics & Automation (Grade 2.3) | 07/2019-07/2023 | Karunya Institute of Technology and Sciences, India (city not specified in source CV) | Robotics & automation |
| Diploma in Electronics & Robotics (89%) | 06/2017-04/2020 | Swamy Abedhanandha Polytechnic College, India | Electronics, robotics fundamentals |

## Professional Experience

### Embedded Systems Developer (Minijob) - Skibbweiss GmbH (03/2025 - present)
Weingarten, Germany
- Upgraded an industrial liquid filling system by replacing legacy controls with a Raspberry Pi Pico controller; designed signal conditioning circuitry between flow meters, solenoid valves, and the MCU
- Validated on breadboard, produced a production-ready PCB in Altium Designer
- Programmed in MicroPython with multi-channel dosing and pulse counting logic

### Field Service Engineer - Lishtong - Apple iPhone Manufacturing (02/2024 - 07/2024)
Bangalore, India
- Installed and configured Cognex vision cameras for automated optical inspection on iPhone production lines
- Supported calibration, testing, and on-site troubleshooting
- Set up feature and defect detection tasks across multiple lines, meeting inspection throughput targets

### Intern - Industrial Automation & Process Control - Yokogawa Electric (07/2023 - 01/2024)
Bangalore, India
- Programmed and configured DCS/PLC systems using ladder logic for industrial process control
- Supported live demonstrations for international clients

## Independent Projects
- **6-DoF Model-Free Pose Estimation (FoundationPose + SAM2)** (05/2026-present): Built a markerless 6-DoF pick-and-place pipeline (SAM2 segmentation + FoundationPose pose estimation) in ROS2 Jazzy on a UR5e arm with a Robotiq 2F-85 gripper, replacing an AprilTag front-end for marker-free pick-and-place with TIAGo; GPU-accelerated inference (RTX 4050) achieves pose estimation within 2-3cm of ground truth with correct orientation. Implemented physics-based grasping in Gazebo Harmonic with MoveIt2 motion planning and contact-based grasp validation using real force feedback; demonstrated closed-loop operation by re-localizing and re-grasping the object from vision alone after placement.
- **Natural Language Robot Control** (2026, github.com/Sammykrishna/nl-robot-control): Built a natural language interface for TurtleBot3 in Gazebo; commands interpreted by Claude AI via the tool_use API, routed to /cmd_vel or Nav2 path planning. Engineered a FastAPI + WebSocket backend with a browser UI (voice input, live mini-map) and a safety layer enforcing velocity clamping and topic whitelisting.
- **Autonomous Pick-and-Place with TIAGo and MoveIt2** (2025, github.com/Sammykrishna/tiago-moveit2-pathplanning): Implemented a full autonomous manipulation pipeline - AprilTag detection, collision-free arm planning via MoveIt2 (OMPL RRTConnect), and pick-and-place in Gazebo; orchestrated 4 containers across 9 Docker Compose service configurations.
- **Sensor Fusion-Based AEB System for ADAS** (2024/2025, github.com/Sammykrishna/carla-aeb-sensor-fusion-opendrive): Engineered an AEB system in CARLA 0.10 fusing YOLOv8 detections with 64-channel LiDAR, achieving 98.3% collision avoidance (59/60 runs) across three Euro NCAP-inspired scenario types; implemented an FSM (Inactive-Warning-Braking) for interpretable braking decisions. Uses OpenCV extensively for image processing throughout the pipeline.
- **3D Vehicle Localisation on KITTI-360** (2024/2025): Combined YOLOv8 segmentation with Velodyne LiDAR point clouds for per-vehicle 3D clustering; implemented camera-LiDAR calibration and a point-in-box ratio metric. Uses OpenCV extensively for image processing throughout the pipeline.

## Technical Skills

### Programming & Robotics
- **Python, C**: primary languages across robotics, embedded, and CV work
- **ROS2**: Nav2, MoveIt2 (OMPL), Gazebo, TurtleBot3, TIAGo, AprilTag, FoundationPose, SAM2
- **Computer Vision / AI**: YOLOv8, PyTorch, OpenCV, camera-LiDAR sensor fusion, Cognex vision systems

### Domain Expertise
- Robotics manipulation & perception (6-DoF pose estimation, grasp planning)
- Embedded systems & control (PCB design, microcontroller firmware, DCS/PLC ladder logic programming)
- Autonomous driving / ADAS (sensor fusion, CARLA simulation)

### Software & Tools
- Docker, CARLA, CUDA, Git, Linux, FastAPI, WebSocket, Altium Designer, MicroPython
- **Mechanical CAD:** AutoCAD, Fusion 360 (B.Tech. Robotics & Automation coursework; no 3D-printing experience on file)

## Publications
None currently.

## Awards
None currently.

## References
None finalized yet - to be added once secured (likely candidates: Skibbweiss GmbH supervisor, an RWU professor, or a manager from the Lishtong/Yokogawa roles).
