The relay board exists to make sure that the flow of power through the boat can be properly controlled in case a shutdown is necessary or to guarantee safety during any fixes of the internal systems (i.e. rewirings or handling the thrusters). Thus, the kill switch board needs to accomplish a few objectives. The first objective is that it needs to be able to initiate a kill through the remote controller or computer. Although a physical kill is required, the relay for that is externally mounted and thus not included on this board. Then, this board must have kill status indicators so that whether it is digitally or physically killed can be indicated to the team (Cornell Autoboat). Lastly, it must most importantly shut down the high power motors. 

<img width="985" height="548" alt="image" src="https://github.com/user-attachments/assets/2bd5a218-8b59-493e-b4e9-e2c05ebd1d3e" />

For the digital kill, it incorporates a GPIO signal from the RP2040 with the 12 V line from the power supply (which is already controlled by the physical kill). By using the GPIO signal to control whether the 12 V line goes through, the relay board enables digital kill functionality. The reason why this implementation includes a charge pump is because the transistor has a gate-source threshold voltage of 1 V. However, the gate-source voltage, without the charge pump, is 3.3 V - 12 V = -8.7 V. The charge pump takes advantage of the 12 V at the source and pumps it to 18 V (16 V to 21 V) which makes the gate-source voltage 6 V.

<img width="975" height="547" alt="image" src="https://github.com/user-attachments/assets/d6f63a0c-6f66-4538-81ba-9c3d948a7fc7" />

The kill status indicators are implemented by feeding the digital (the GPIO output) and physical (the power distribution output) kill signals to separate LEDs and pairing the LEDs with current limiting resistors. The transistor shown here is meant to allow for a signal to be sent to the computer when a kill is executed. Thus, it 

<img width="980" height="546" alt="image" src="https://github.com/user-attachments/assets/72adfbd0-c03e-4718-8ae5-d26937e9ea60" />

<img width="1150" height="780" alt="image" src="https://github.com/user-attachments/assets/af1ea010-ac4c-4846-bf67-916eb14904dc" />
