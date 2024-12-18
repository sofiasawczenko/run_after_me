# CoppeliaSim Robot Deviation Simulation with Laser Data Processing

This project demonstrates the integration of a Python script with the CoppeliaSim (formerly V-REP) simulation platform using the Remote API. The script allows controlling a Pioneer P3-DX robot, retrieving data from a Hokuyo laser sensor, and processing this data for navigation. **The primary goal of this project is simulating the deviation of a virtual robot in Python using the CoppeliaSim platform**. Through this simulation, the robot is programmed to navigate its environment while avoiding obstacles using sensor data. The script manages robot movement, processes laser data, and adjusts the robot's velocity to navigate around detected obstacles.

## Features

- Connect to CoppeliaSim through the Remote API server.
- Retrieve laser range and angle data from the Hokuyo sensor attached to the robot.
- Process laser data to detect obstacles and adjust robot movement accordingly.
- Visualize laser data using Matplotlib.
- Control the robot's velocity and movement based on the laser sensor readings.

## Prerequisites

To run this project, you need the following:

- **CoppeliaSim**: Download and install CoppeliaSim (formerly V-REP) from [here](https://www.coppeliarobotics.com/).
- **Python 3.x**: Install Python from [here](https://www.python.org/downloads/).
- **Matplotlib**: Install using `pip install matplotlib`.
- **NumPy**: Install using `pip install numpy`.

Ensure that you have access to the `sim.py` file (provided by CoppeliaSim) in your project directory for the Remote API to work.

## Setup Instructions

1. **Install CoppeliaSim**: Make sure CoppeliaSim is installed and configured on your system.
2. **Start the Remote API Server**:
   - Open the CoppeliaSim simulation and run the Remote API server by using the `simRemoteApi.start(19999)` command in the CoppeliaSim script editor or via the CoppeliaSim UI.
   
3. **Clone or Download the Python Script**:
   - Clone or download the provided Python script to your local machine.

4. **Run the Python Script**:
   - Ensure CoppeliaSim is running and the Remote API server is active.
   - Run the Python script using `python3 script_name.py`.
   
5. **Observe the Output**:
   - The robot will move around based on its sensor readings.
   - A plot of the laser sensor data will be displayed during the simulation.

## Script Breakdown

### 1. **Connecting to the CoppeliaSim Remote API**
   - The script connects to CoppeliaSim on `127.0.0.1` using port `19999` and initializes a connection with the robot (`Pioneer_p3dx`).

### 2. **Reading Sensor Data**
   - The `readSensorData` function retrieves laser sensor data (`hokuyo_range_data` and `hokuyo_angle_data`) from the simulation.
   - The data is unpacked and returned for further processing.

### 3. **Laser Data Visualization**
   - The `draw_laser_data` function visualizes the laser sensor data in a 2D polar plot using Matplotlib.

### 4. **Robot Movement Control**
   - The robot’s velocity and angular velocity are computed based on the sensor data.
   - The robot adjusts its movement (linear and angular velocities) when obstacles are detected in the laser data.
   - The robot's wheels are controlled using the Remote API to set target velocities for the left and right motors.

### 5. **Simulating for 60 Seconds**
   - The script runs for 60 seconds, continuously reading sensor data, processing it, and adjusting the robot’s movements.

### 6. **Stopping the Robot and Simulation**
   - After 60 seconds, the robot stops, and the simulation is halted.

## Dependencies

- `sim` (CoppeliaSim Remote API library)
- `numpy`
- `matplotlib`
- `time`

## Troubleshooting

- **"sim.py" could not be imported**: Ensure that `sim.py` is in the same directory as your script, or adjust the `PYTHONPATH` environment variable accordingly.
- **Connection Issues**: Ensure that the Remote API server in CoppeliaSim is running, and the correct port is specified in the script.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
