# Gogogo
Gold Files
package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.HardwareMap;
import com.qualcomm.robotcore.hardware.Servo;


public class Robo_tings {

        DcMotor Arm;
        DcMotor FrontLeft;
        DcMotor BackLeft;
        DcMotor FrontRight;
        DcMotor BackRight;
        Servo Right;
        Servo Left;
        private double armPos;
        static int ticksPerRev = 1440;
        static double armTop = 10;

        public void hardware(HardwareMap hardwareMap) {
            FrontLeft = hardwareMap.get(DcMotor.class, "FrontLeft");
            BackLeft = hardwareMap.get(DcMotor.class, "BackLeft");
            FrontRight = hardwareMap.get(DcMotor.class, "FrontRight");
            BackRight = hardwareMap.get(DcMotor.class, "BackRight");
            Right = hardwareMap.get(Servo.class, "Right");
            Left = hardwareMap.get(Servo.class, "Left");
            Arm = hardwareMap.get(DcMotor.class, "Arm");

            Arm.setMode(DcMotor.RunMode.RUN_USING_ENCODER);

            FrontLeft.setDirection(DcMotor.Direction.REVERSE);
            BackLeft.setDirection(DcMotor.Direction.REVERSE);
        }

        public void Forward(double Power){
            FrontLeft.setPower(Power);
            FrontRight.setPower(Power);
            BackLeft.setPower(Power);
            BackRight.setPower(Power);

        }
        public void TurnLeft(double Power) {
            FrontLeft.setPower  (Power);
            FrontRight.setPower (-Power);
            BackLeft.setPower (Power);
            BackRight.setPower (-Power);
        }
        public void TurnRight(double Power) {
            FrontLeft.setPower  (-Power);
            FrontRight.setPower  (Power);
            BackLeft.setPower  (-Power);
            BackRight.setPower  (Power);

        }


    public void encodersForward(double inches, double power) {
        FrontLeft.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        FrontRight.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        BackLeft.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        BackRight.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);



        FrontLeft.setTargetPosition((int) inchesToTicks(inches));
        FrontRight.setTargetPosition((int) inchesToTicks(inches));
        BackLeft.setTargetPosition((int) inchesToTicks(inches));
        BackRight.setTargetPosition((int) inchesToTicks(inches));

        FrontLeft.setMode(DcMotor.RunMode.RUN_TO_POSITION);
        FrontRight.setMode(DcMotor.RunMode.RUN_TO_POSITION);
        BackLeft.setMode(DcMotor.RunMode.RUN_TO_POSITION);
        BackRight.setMode(DcMotor.RunMode.RUN_TO_POSITION);

        FrontLeft.setPower(power);
        FrontRight.setPower(power);
        BackLeft.setPower(power);
        BackRight.setPower(power);

        while (FrontLeft.isBusy() && FrontRight.isBusy() && BackLeft.isBusy() && BackRight.isBusy()) {

        }

        Stop();
    }


    public void encodersTurnLeft (double power, int distance){

        FrontLeft.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        FrontRight.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        BackLeft.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        BackRight.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);

        FrontLeft.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        FrontRight.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        BackLeft.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        BackRight.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
    }

    public void Stop () {
        FrontLeft.setPower(0);
        FrontRight.setPower(0);
        BackLeft.setPower(0);
        BackRight.setPower(0);
    }

    //ticks are 1440

    public double inchesToTicks(double inches) {
            // this is the circumference of your wheels
            double circumference = 4*Math.PI;
            double Johnson = 1440;
            return (int) (inches * Johnson/circumference);
    }
    double ticksToInches(double ticks, double radius) {
            return ticks/ticksPerRev*(radius*2*Math.PI);
    }



    public void ArmUp ( double Power) {
        while (armPos < 1){
            Arm.setPower(1);
            updateArmPos();
        }
    }

    public void ArmDown ( double Power) {
        while (armPos >= 1){
            Arm.setPower(-1);
            updateArmPos();
        }
    }


    void updateArmPos(){
            armPos += ticksToInches(1440,10);
    }


    public void Backwards (double Power) {
        FrontLeft.setPower(-1);
        FrontRight.setPower(-1);
        BackLeft.setPower(-1);
        BackRight.setPower(-1);
    }
}









