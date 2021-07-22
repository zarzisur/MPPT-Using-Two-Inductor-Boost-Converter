# MPPT-Using-Two-Inductor-Boost-Converter

The two inductor boost converter is an isolated topology. Its circuit diagram is like this:
![simulink](https://user-images.githubusercontent.com/35787202/126601790-6355d0fa-fcaf-478e-a6e8-5968deddc6fc.png)

To analysis two inductor boost converter we have to keep in mind:
	Input side current is controlled by inductor and there is no interference from output. Output current is a reflected part of input current.
	Secondary voltage is controlled by rectifier capacitor voltage. Primary terminal voltage is a reflected part of secondary terminal voltage.
Let us assume after going to steady state, single capacitor voltage= V_o/2.
Input voltage= V_in.
Input Inductor currents are iL_1 and iL_2.
Both of the switch should not be off at any time to give a path to flow inductor current.
There can be three configuration:
S1 and S2 both are on:
Voltage across  both inductor is Vin. There is no current flowing into the primary coil. Secondary coil does not develop any voltage. Secondary is decoupled from primary. Load take energy from output capacitor. Voltage of output cap decrease slightly depeding on current drawn by the load.

S1 OFF and S2 ON:
 L2 keeps charging. As S1 is off inductor L1  inject current to the primary coil. Secondary coil generate reflected current , so  it is certain that D1 will be forward biased no matter what is the voltage of  C1 . Ignoring the diode drop, secondary coil voltage is equal to C1`s voltage. Primary voltage will be reflected part of secondary voltage. So, this reflected secondary voltage or we can say primary voltage will decide the slope of L1 inductor current change. If primary voltage is lower than input voltage then L1`s current will rise with positive slope. If primary voltage is higher than the input voltage then inductor current change  will have negative slope.

So, primary voltage V_p=V_c1/n;
Where, V_c1=V_o/2  and n=Ns/Np ; 
So, V_p=V_o/2n;
Voltage across inductor L1=V_in-V_p=V_in-V_o/2n;

S1 ON and S2 OFF:
Inductor L1 charges . As switch S2 is off so, inductor L2 put current in the primary winding. To flow reflected current to secondary winding D2 will be forward biased. Voltage of capacitor 2 will be secondary voltage. Primary voltage will be reflected part of the secondary voltage. 
Vp=-V_c2=-V_o/2;
Voltage across inductor L1= Vin;

Let us define duty cycle D= Ton/ T; 
Applying volt second balance in the inductor L1,
V_in*DT+(V_in-Vp)*(1-D)T=0;
V_in*DT+(V_in-V_o/2n)*(1-D)T=0;
V_in=V_0/2n*(1-D);
So,V_o=(2*n*V_in)/(1-D).

