# Gogogo
Gold Files
package org.firstinspires.ftc.teamcode;

        import com.qualcomm.robotcore.eventloop.opmode.OpMode;
        import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
        //import com.qualcomm.robotcore.hardware.DcMotor;
        //import com.qualcomm.robotcore.hardware.HardwareMap;

@TeleOp (name = "Justin's Jeans")
public class Gold_Tele extends OpMode {
;
    Robo_tings robo_tings = new Robo_tings();

    @Override
    public void init(){
        gamepad1.setJoystickDeadzone(0.1f);
        gamepad2.setJoystickDeadzone(0.1f);

        robo_tings.hardware(hardwareMap);
    }

    @Override
    public void loop() {



        double LeftStickY = -gamepad1.left_stick_y;
        double RightStickY = -gamepad1.right_stick_y;

        robo_tings.FrontLeft.setPower(LeftStickY);
        robo_tings.BackLeft.setPower(LeftStickY);
        robo_tings.FrontRight.setPower(RightStickY);
        robo_tings.BackRight.setPower(RightStickY);


        if(gamepad2.left_bumper){
            robo_tings.Arm.setPower(0.5);
        }
        else if(gamepad2.right_bumper) {
            robo_tings.Arm.setPower(-0.5);
        }
        else{robo_tings.Arm.setPower(0);}


        if (gamepad2.y) {
            robo_tings.Right.setPosition(0);
            robo_tings.Left.setPosition(1);
        }else if ( gamepad2.x ) {
            robo_tings.Right.setPosition(0.2);
            robo_tings.Left.setPosition(0.8);
        } else if ( gamepad2.a) {
            robo_tings.Right.setPosition(0.8);
            robo_tings.Left.setPosition(0.2);
        } else if(gamepad2.b)  {
            robo_tings.Right.setPosition(0.4);
            robo_tings.Left.setPosition(0.6);
        }
    }
}

       // if (gamepad2.dpad_up) {
          //  robo_stuff.Left.setPosition(0.6);
        // else if ( gamepad2.dpad_left || gamepad2.dpad_right) {
           // robo_stuff.Left.setPosition(0.8);
        // else if ( gamepad2.dpad_down) {
           // robo_stuff.Left.setPosition(0.2);












