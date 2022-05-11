# CAN Bus Motor Controllers
CAN bus is another way of connecting motors to the RoboRIO. Instead of connecting in parallel to the PWM ports, CAN motors are connected to the CAN bus in series. They must be configured in the Phoenix software, and using the Java API requires the vendor library to be installed.

## Installing the software
At least one person on the team needs to have the CTRE electronics software installed on their laptop.
[!ref](/code/software)

## Using the software

### Connecting to the RoboRIO through the CTRE Phoenix software
1. Open Phoenix Tuner
2. Connect the laptop to the robot over USB. The RoboRIO has a USB-B port on it, and is the port that should be used.
3. In the Phoenix Tuner software, select the CAN Bus tab.
4. When finished, click the restart robot code button.

### Configuring the CAN Bus
#### Identifying devices
!!!warning TODO
!!!
#### Changing the device name and ID
!!!warning TODO
!!!
#### Upgrading the device firmware
!!!warning TODO
!!!

## Installing the WPILib vendor library
!!!info
Note that using the online vendor library requires an internet connection.
!!!
1. Click the W icon in the top-right corner of WPILib VSCode.
2. Choose Manage Vendor Libraries
3. Choose 'Install New Libraries'
    a. If you have the Phoenix software installed, use offline and select the 'CTRE-Phoenix'.
    b. Otherwise, use online, and use the url found on [this page](https://docs.ctre-phoenix.com/en/stable/ch05a_CppJava.html#frc-c-java-add-phoenix).

## Using the WPILib vendor library
Once the vendor library is installed, you can use CAN motors (like the TalonSRX) the same as any other motor controller. For the motor port, use the CAN ID assigned in the Phoenix software.

[!ref](/code/components/pwm_motor_controllers.md)