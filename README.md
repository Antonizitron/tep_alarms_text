# Tennessee Eastman Process Alarms in Text Format
The datasets represents Industrial Control System's (ICS) Alarms in text format, recreated from "Tennessee-Eastman-Process" Alarm Management Dataset:
Gianluca Manca, November 1, 2020, ""Tennessee-Eastman-Process" Alarm Management Dataset", IEEE Dataport, doi: https://dx.doi.org/10.21227/326k-qr90.

Original work is based a process proposed by J.J. Downs and E.F. Vogel in 1993 in a publication "A plant-wide industrial process control problem", with changes by A. Bathelt, N. Lawrence Ricker and M. Jelali, “Revision of the Tennessee Eastman Process Model” and E. Arroyo, “Capturing and Exploiting Plant Topology and Process Information as a Basis to Support Engineering and Operational Activities in Process Plants”.
The Tennessee-Eastman-Process simulates the production of two products (G and H) from four reactants (A, C, D, and E). It includes five major units:
- Reactor
- Condenser
- Vapor/liquid separator
- Recycler compressor
- Product stripper

The simplified P&ID:
<br>
![alt TEP P&ID](https://github.com/Antonizitron/tep_alarms_text/blob/main/resources/tep_pnid.PNG?raw=true)
<br>

The dataset published by IEEE contains results of process simulation in a normal stady state and abnormal conditions with Active Root Cause and Normalizarion phases. While former simualtion did not have any alarms, later one generated good number of messages. Remaingin portion of work described alarms management approached aimed to reduce number of neusance alarms.

The dataset orginized in 3 csv files, simialr to origianl work:
- Original: contains alarms from all 100 Test Cases with no Alarm Management technics
- Filtered: alarms with implemened filters
- Deadband: alarms with implemened deadbands

Each csv file have 5 columns:
- timestamp: timestamp of the alarm. Started selected arbitrary and can easily be changed.
- tag: tag name caused an alarm.
- type: type of alarm. Can be one of 8 values (please note that in any point of time tag can be in only 1 type of alarm):
    * LL: Low Low alarm
    * L: Low alarm
    * H: High alarm
    * HH: High High alarm
    * LL NR/L NR/H NR/HH NR: Recovery messages of appropriate alarms (when for example Process Variable becomes higher than Low alarm setpoint, the system generates L NR message)
