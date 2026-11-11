# Robot
# Project Overview
This repository contains the complete CAD designs, STM32 HAL source code, and presentation materials for an autonomous differential-drive mobile robot developed for the ELE00098H module at the University of York. Built around the York Engineering Embedded Platform (YEEP-144) featuring an STM32H563ZI microcontroller, the robot is designed to map unknown maze environments, navigate around obstacles, track encoder odometry, and locate infrared-emitting beacons to interact with them in numerical sequence.
# Key Technical Specifications
Main Controller: York Engineering Embedded Platform (YEEP-144) featuring an STM32H563ZI MU
Drive System: Pololu TB6612FNG dual motor driver
Actuation & Encoders: Dual micro-metal gearmotors equipped with quadrature encoders for wheel position tracking
Distance Sensing: HC-SR04 ultrasonic range sensors and Sharp GP2Y0E02B IR distance sensors (I2C/Analog)
Signal Receiver: TSOP4838 38kHz IR receiver module for parsing beacon identification signals
Mechanical Structure: Custom 2D laser-cut chassis, 3D-printed mounting brackets, custom wheels, and caster wheel
# Project Implementation Phases
Phase 1: Custom Chassis Construction
- Mechanical Layout: Two-wheel differential drive setup supported by a rear caster wheel for smooth turning.
- Design Optimization: Engineered for structural rigidity, minimal material thickness, simple assembly, and quick battery access.
- Fabrication: Designed using 2D/3D CAD software and manufactured using laser cutting and 3D printing tools.
Phase 2: Reactive Navigation and Obstacle Avoidance
- Sensor Processing: Continuous polling of distance data from both ultrasonic and IR range sensors.
- Motor Control: Closed-loop algorithms implemented directly on the STM32 HAL to adjust wheel speeds dynamically.
- Collision Prevention: Steers around barriers in real time to navigate tight corridors and avoid becoming stuck on walls.
Phase 3: Odometry and Spatial Mapping
- Pose Estimation: Tracks $X, Y, \theta$ coordinates in real time using hardware timer encoder peripherals.
- Spatial Mapping: Synchronizes distance sensor readings with estimated coordinates to record wall locations and open paths.
- Data Structure: Maintains an internal map format to inform autonomous path planning decisions across the arena.
Phase 4: Beacon Detection and Sequential Interaction
- Beacon Parsing: Decodes 38kHz IR signal patterns using the Vishay TSOP4838 receiver to identify beacon IDs.
- Path Planning: Plots efficient routes to return to mapped beacon coordinates in strict numerical order.
- Physical Interaction: Executes controlled forward contact to physically push each beacon once reached.
