---
order : 7
---
# Commands and Subsystems
The primary function of the robot is controlled by commands and subsystems. 

## Subsystems
Subsystems define the overarching structure of the robot, encapsulating motors, solenoids, and some sensors. Additionally, subsystems abstract the operation of motors and solenoids, making the code more readable and easier to maintain.

```java Example Subsystem
public class DriveSubsystem extends SubsystemBase {
	//Here we define our motors
	public final SpeedController m_motorFL = new VictorSP(MotorPorts.kMotorFLPort);
	public final SpeedController m_motorRL = new WPI_VictorSPX(MotorPorts.kCanMotorRLPort);

	public final SpeedController m_motorFR = new VictorSP(MotorPorts.kMotorFRPort);
	public final SpeedController m_motorRR = new WPI_VictorSPX(MotorPorts.kCanMotorRRPort);

	//Here we define our motor groups, left and right
	public final SpeedControllerGroup m_LMotors = new SpeedControllerGroup(m_motorFL, m_motorRL);
	public final SpeedControllerGroup m_RMotors = new SpeedControllerGroup(m_motorFR, m_motorRR);

	//Here we create our drive train
	private final DifferentialDrive m_transmission = new DifferentialDrive(m_LMotors, m_RMotors);

	/**
	 * Moves the robot using tank drive
	 * @param left The speed of the left motors
	 * @param right The speed of the right motors
	 */
	public void drive(double left, double right) {
		m_transmission.tankDrive(left, right);
	}
}
```

## Commands
Commands are the primary way that the robot will be controlled. They take in controller and sensor input, and then use the input to control the robot through the subsystems.

Method | Returns | Use | Requirements
--- | --- | --- | ---
constructor | N/A | Creates a new instance of the command. | Must call `addRequirements(subsystem)` for each subsystem that the command uses
initialize() | void | Runs when the command is first initialized. | None
execute() | void | Runs every tick the command is running. | None
end() | void | Runs when the command is finished. | None
isFinished() | boolean | Returns true if the command is finished. Usually only used for autonomous commands. | None

```java Example Command
public class ExampleCommand extends CommandBase {

	private final DriveSubsystem driveSubsystem;
	private final double speed = 0.5;

	public ExampleCommand(DriveSubsystem driveSubsystem) {
		this.driveSubsystem = driveSubsystem;

		addRequirements(driveSubsystem);
	}

	@Override
	public void initialize() {
	}

	@Override
	public void execute() {
		// Get the input from the controller (x-axis). Goes from -1 to 1
		double controllerInput = Joysticks.xboxController.getRawAxis(0);
		// Tell the drive train to turn based on the speed and the controller input
		driveSubsystem.drive(speed * controllerInput, -speed * controllerInput);
	}

	@Override
	public void end(boolean interrupted) {
	}

	@Override
	public boolean isFinished() {
		return false;
	}
}
```

### Registering Teleop Commands
All registration for commands and subsystems is done through the `RobotContainer` class. See the example below:

```java RobotContainer.java
public class RobotContainer {
	private final DriveSubsystem driveTrain = new DriveSubsystem();

	public RobotContainer() {
        ...
		driveTrain.setDefaultCommand(new ExampleCommand(driveTrain));
	}
	...
}
```

## Autonomous Commands
!!!danger
Taking input from the driver during autonomous violates the rules of the competition, and penalties will be given to the team.
!!!
Autonomous commands are commands that are run automatically during the autonomous period. They can only use sensors and cameras to navigate and score points. 

Autonomous commands are created in the same way as teleop commands, but are registered differently.

### Registering Autonomous Commands
As with teleop commands, all registration for commands and subsystems is done through the `RobotContainer` class. However, instead of being registered through the constructor, autonomous commands are registered through the `RobotContainer.getAutonomousCommand()` method.

!!!info Note
In order for the AutonomousCommand to work through the `getAutonomousCommand()` method, a Robot.java should use the default `autonomousInit()` method.
==- Default `autonomousInit()` method
```java
public void autonomousInit() {
    m_autonomousCommand = m_robotContainer.getAutonomousCommand();

    // schedule the autonomous command (example)
    if (m_autonomousCommand != null) {
        m_autonomousCommand.schedule();
    }
}
```
===
!!!

```java RobotContainer.java
public class RobotContainer {
	private final DriveSubsystem driveTrain = new DriveSubsystem();

    ...
	
	public Command getAutonomousCommand() {
        return new AutonomousCommand(driveTrain);
	}
}
```
