# PWM Motor Controllers
Motor controllers are responsible for controlling the speed of a motor. In code, they are based on the interface `SpeedController` with implementations including `VictorSPX`, `Spark`, and `TalonSRX`.

!!!info Note
The motor controller used on the physical robot ***must*** be the same as the one used in the code.
!!!

## Defining PWM Motor Controllers
All motor controllers should always be defined within a subsystem. This allows the code to remain operate, and allows for multiple commands to use the same motor.

Motors should be defined as a property of the class, and should always be private.
```java Example Subsystem
public class ExampleSubsystem extends SubsystemBase {
    private SpeedController m_motor = new VictorSP(Constants.motorPWMPort);

    ...
}
```

Motors should then have their functionality defined by a method in the subsystem.
```java Example Subsystem
public class ExampleSubsystem extends SubsystemBase {
    ...

    public void spinLeft() {
        m_Motor.setSpeed(-1.0);
    }

    public void spinRight() {
        m_Motor.setSpeed(1.0);
    }

    public void stop() {
        m_Motor.setSpeed(0.0);
    }

    public void setSpeed(double speed) {
        m_Motor.setSpeed(speed);
    }
}
```