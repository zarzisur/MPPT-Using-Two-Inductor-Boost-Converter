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



## Design of Isolated Two Inductor Boost Converter for High voltage Gain Photovoltaic Application


Maximum Power=	213.5 Watt.
Open Circuit Voltage, Voc/ Maximum Input Voltage=36.3V.
Min Input Voltage=25V.
Voltage at maximum power point, Vmp=29V.
Short Circuit Current ,Isc=7.84.
Current at maximum power point, Imp=7.35.
Maximum Output Voltage=450V.
Minimum Output Voltage=370V.
Switching Frequency =100Khz.


The equation for output voltage ,
V_o=(2*V_in*n)/((1-D) ).
Where, n= turn ratio = Ns/Np.
Selection of Inductor:
L=(V_in(min) *D_SW(max) )/(ΔI_ind*f_sw ).
V_in(min) =25V.
D_SW(max) =0.9.
f_sw=100Khz.
ΔI_ind=10% of I_sc=.1*7.84=.784A.
So,L=(25*0.9)/(.784*100000)=287uH.
We are taking value L1=L2=300 micro Henry.
Selection of Capacitor output :
Output Capacitor values are calculated using these equations:
C≥(I_0*D*T_sw)/ΔV_max 
 For I_o=10 Amps,D=0.9 and T_sw=1/100000 and deltaV_max=0.5V;
C should be greater then 180 micro Farad .We are using 470 micro Farad

High Frequency Transformer Design:
The number of primary turn , N_p=(V_in*D_max)/(f_sw*ΔB*A_c )
The number of secondary turn, N_s=n*N_P
Where, ΔB  denotes the flux density and is assumed to be equal 0.2 Tesla
The area product of the cross sectional area and window area is expresses as follow:
A_p=(0.5*P_o)/(√2*K_w*J*f_s*B_m )
K_w=wimdow factor=0.4 typical,
J=current density=3*10^6  A/m^2 ,  
B_m=0.2 Tesla for ferrite core, 
f_s=switching frequency=my design specification,
P_o=output power=my design specification







###Loss analysis of MOSFET and Diode:

The losses of mosfet and diode can be classified into 2 parts: conduction loss and switching loss.
Switching loss,P_sw=(V_DS*I_D*t_sw (off))/(2*T_sw ).
t_sw (off)=time taken to turn off a switch.

The conduction loss of the MOSFET is ,
P_conduction=1.6*R_ds(on) *I_rms^2

Switching loss of the diode is:
P_sw (diode)=(V_BR*I_RM*t_rr)/(2*T_sw ).
Where, Vbr= maximum breakdown voltage
Irm=reverse recovery current
Trr=reverse recovery time
 The conduction loss of the diode is,
P_con=1.16*I_D(avg) +0.053*I_(D(rms))^2.
Where, Id(avg)= average diode current.
And, Id(rms)= root mean square current value.


# Design of Current fed push pull converter:
Equation for output voltage, 
V_o=n*V_in/(2*(1-D)).
Where n=Ns/Np;
Design of Inductor:
 I_in=P_o/(V_in*η)
Where , η=efficiency

Inductance value, L=V_o/(16*n*f_s*〖ΔI〗_max ).

## Design of Transformer:
Primary winding can be determined using this equation:
N_P=(V_o*(1-D))/(n*A_C*B_m*f_s ).
Secondary winding  can be determined using this equation:
					
N_P=(V_o*(1-D))/(A_C* B_m* f_s ).

Output Value of the capacitor:
C=(P_o*(2D-1))/(4*y*V_o^2*f_s ).
Where, 
C=output capacitor
Po=output power
y=Percentage of output voltage ripple
Vo= Output voltage
fs = switching frequency


