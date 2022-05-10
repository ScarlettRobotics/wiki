---
order: 8
---
# Project Structure
The robot code is split into a variety of files. The purpose of each file is as follows:

+++ RobotContainer.java
!!!
The bulk of the robot functionality should be defined in this file. 
!!!
Here, commands and subsystems are instantiated and configured.

---

**Example:**
```java RobotContainer.java
private final DriveSubsystem driveTrain = new DriveSubsystem();

public RobotContainer() {
    driveTrain.setDefaultCommand(new ExampleCommand(driveTrain));
}

public Command getAutonomousCommand() {
    return new AutonomousCommand(driveTrain);
}
```
---

[!ref text="Learn More"](/code/commands_and_subsystems)
+++ Constants.java
This file should be used to define important values critical to the robot's operation.
Values that should be defined here include: 
* Motor ports
* Sensor ports 
* Joysticks

---

**Example:**
```java Constants.java
public class Constants {
    public static class MotorPorts {
        public static final int driveTrain_FL = 1;
        public static final int driveTrain_RL = 11;
        public static final int driveTrain_FR = 0;
        public static final int driveTrain_RR = 10;
    }

    public static class Joysticks {
        public static final Joystick xboxController = new Joystick(0);
    }
}
```
+++ Robot.java
This file is the main code for the robot. You will mostly be using commands and subsystems to define the behavior of the robot, but this file can be used for any initialization code, or any code that always needs to be run.

---

**Available Methods:**

Method | Use
--- | ---
robotInit() | Called when the robot is first started up. Best used for any extra initialization code.
robotPeriodic() | Called every tick the robot is in an active state. This function must call `CommandScheduler.getInstance().run()`
disabledInit() | Called when the robot is disabled. Add any necessary cleanup code here.
disabledPeriodic() | Called every tick the robot is disabled. It is against the rules to interact with any subsystems here.
autonomousInit() | Called when autonomous mode is enabled.
autonomousPeriodic() | Called every tick the robot is in autonomous mode.
teleopInit() | Called when teleop mode is enabled.
teleopPeriodic() | Called every tick the robot is in teleop mode.
testInit() | Called when test mode is enabled.
testPeriodic() | Called every tick the robot is in test mode.

+++ Main.java
!!!danger
This file should not be modified.
!!!
Main.java is the main file that is run when the robot is started.

---

**Default Value:**
```java Main.java
public final class Main {
	private Main() {
	}

	public static void main(String... args) {
		RobotBase.startRobot(Robot::new);
	}
}
```
+++

## Example Project
A basic example project can be found on the Scarlett Robotics GitHub organization. 

[!button text="Example Project" icon="arrow-right" iconAlign="right"](https://github.com/ScarlettRobotics/RecruitRIOProgram/tree/master/2022_Intro_Example)