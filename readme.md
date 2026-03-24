# Accelerometer Music

A web application that visualizes linear acceleration using the device's accelerometer and calculates speed in real-time.

## Overview

This project utilizes the DeviceMotionEvent API to access the device's accelerometer data and provides visual feedback through animated bars representing X, Y, and Z axis acceleration values. It also calculates the current speed based on the acceleration data.

## Features

- **Real-time Acceleration Visualization**: Three vertical bars display the current linear acceleration for X, Y, and Z axes
- **Kalman Filtering**: Uses kalmanjs to filter raw accelerometer data for smoother readings
- **Speed Calculation**: Calculates and displays current speed in meters per second based on Z-axis acceleration
- **Direction Change Detection**: Automatically handles speed calculation when acceleration direction changes
- **Cross-axis Support**: Visualizes all three acceleration axes (X, Y, Z)

## How It Works

### Acceleration Visualization

The application uses vertical bars that grow upward (positive values, shown in green) or downward (negative values, shown in red) based on the acceleration value. The bars are normalized to a range of -1 to 1, with a maximum expected acceleration value of 10 m/s².

### Kalman Filtering

Raw accelerometer data is filtered using a Kalman filter (from kalmanjs) with the following parameters:
- R (Measurement Noise): 0.01
- Q (Process Noise): 3

This helps reduce noise and provide smoother acceleration readings.

### Speed Calculation

Speed is calculated using the following approach:
1. Track the time delta between acceleration samples
2. Calculate the change in speed using: `deltaSpeed = |acceleration.z| * deltaTime`
3. Detect direction changes to properly handle speed increase/decrease
4. Ensure speed never goes below 0

## Browser Compatibility

The application requires the DeviceMotionEvent API, which is supported on:
- Mobile devices (iOS and Android)
- Some desktop browsers with accelerometer support

If DeviceMotionEvent is not supported, the application displays a message indicating the lack of support.

## Usage

1. Open `index.html` in a web browser (preferably on a mobile device)
2. Allow access to motion sensors when prompted
3. Move the device to see the acceleration bars respond
4. View the current speed calculation at the bottom of the page

## Technical Details

### File Structure

```
accelormeter-music/
├── index.html      # Main application file
├── readme.md       # This documentation
├── blog/           # Blog articles
│   ├── index.html  # Blog listing page
│   ├── article1.html
│   └── article2.html
```

### Technologies Used

- HTML5
- CSS3 (transitions, animations)
- JavaScript (ES6+)
- [kalmanjs](https://unpkg.com/kalmanjs) - Kalman filter library

## License

MIT License
