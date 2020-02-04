# Gogogo
Gold Files

package org.firstinspires.ftc.teamcode;
import com.qualcomm.robotcore.eventloop.opmode.Autonomous;
import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;

@Autonomous (name = "GailGAleGayle")


public class GayleeSupreme extends LinearOpMode {

    Robo_tings robo_tings = new Robo_tings();

    @Override
    public void runOpMode() {

        robo_tings.hardware(hardwareMap);

        waitForStart();

        robo_tings.encodersForward(40, 1);
        robo_tings.encodersForward(-40, 1);
    }
}






