# PWM Motor Controllers
Motor controllers are responsible for controlling the speed of a motor. In code, they are based on the interface `MotorController` with implementations including `VictorSPX`, `Spark`, and `TalonSRX`.

!!!info Note
The motor controller used on the physical robot ***must*** be the same as the one used in the code.
!!!

## Defining PWM Motor Controllers
All motor controllers should always be defined within a subsystem. This allows the code to remain operate, and allows for multiple commands to use the same motor. The constructor for the motor controller takes in the physical port the controller is plugged into on the RoboRIO.

Motors should be defined as a property of the class, and should always be private.
```java Example Subsystem
public class ExampleSubsystem extends SubsystemBase {
    private MotorController m_motor = new VictorSP(Constants.motorPWMPort);

    ...
}
```

Motors should then have their functionality defined by a method in the subsystem.
```java Example Subsystem
public class ExampleSubsystem extends SubsystemBase {
    ...

    public void spinLeft() {
        m_Motor.set(-1.0);
    }

    public void spinRight() {
        m_Motor.set(1.0);
    }

    public void stop() {
        m_Motor.set(0.0);
    }

    public void setSpeed(double speed) {
        m_Motor.set(speed);
    }
}
```

## Interacting with PWM Motor Controllers
PWM motor controllers are controlled by setting the speed of the motor. A list of methods that can be used with Speed Controllers are as follows:

Method | Parameters | Returns | Use
--- | --- | --- | ---
set() | `double speed`{:.java} |  | Sets the speed of the motor
get() |  | `double speed` | Gets the speed of the motor
setInverted() | `boolean inverted` |  | Sets whether the motor is inverted
getInverted() |  | `boolean inverted` | Gets whether the motor is inverted
stopMotor() | | | Stops the motor

## Controller Groups
Controller groups allow you to control multiple motors at the same time. Controller groups are defined as follows:
```java
// Define the individual motors
MotorController frontMotor = new VictorSP(Constants.frontMotorPort);
MotorController backMotor = new VictorSP(Constants.backMotorPort);

//Define the motor group
MotorControllerGroup motors = new MotorControllerGroup(frontMotor, backMotor);
```

!!!info
Motor controller groups are used in the same way as a regular motor controller.
!!!

### Differential Drive
Differential drives are used often for the robot's drive train. It provides an interface for common forms of drive, such as tank drive and arcade drive.

```java
// Define the individual motors
MotorController frontLeftMotor = new VictorSP(Constants.frontLeftMotorPort);
MotorController frontRightMotor = new VictorSP(Constants.frontRightMotorPort);
MotorController backLeftMotor = new VictorSP(Constants.backLeftMotorPort);
MotorController backRightMotor = new VictorSP(Constants.backRightMotorPort);

// Define the motor groups
MotorControllerGroup leftMotors = new SpeedControllerGroup(frontLeftMotor, backLeftMotor);
MotorControllerGroup rightMotors = new SpeedControllerGroup(frontRightMotor, backRightMotor);

// Define the differential drive
DifferentialDrive driveTrain = new DifferentialDrive(leftMotors, rightMotors);
```

Drive Type | Description
--- | ---
Tank Drive | Tank drive controls the left and right sides in absolute speed. It is the equivalent of controlling the left and right motor groups separately. <br> `driveTrain.tankDrive(leftSpeed, rightSpeed)`
Arcade Drive | Arcade drive controls the robot using speed and rotation. The robot moves at the speed and rotates at the rate specified. <br> `driveTrain.arcadeDrive(speed, rotation)`