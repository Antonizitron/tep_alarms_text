# Industrial Control System (ICS) Alarm Text Dataset - Based on Tennessee Eastman Process
This repository provides a textual dataset of Industrial Control System (ICS) alarms, derived from the "Tennessee-Eastman-Process" Alarm Management Dataset by Gianluca Manca (2020): "Tennessee-Eastman-Process" Alarm Management Dataset, IEEE Dataport.

## Origin and Process Description
The original work is based on a process proposed by J.J. Downs and E.F. Vogel in 1993 ("A plant-wide industrial process control problem"), with subsequent modifications by A. Bathelt, N. Lawrence Ricker, M. Jelali (“Revision of the Tennessee Eastman Process Model”) and E. Arroyo (“Capturing and Exploiting Plant Topology and Process Information as a Basis to Support Engineering and Operational Activities in Process Plants”).

The Tennessee-Eastman-Process (TEP) simulates the production of two products (G and H) from four reactants (A, C, D, and E) and comprises five major units:
- Reactor
- Condenser
- Vapor/liquid separator
- Recycler compressor
- Product stripper
<br>
![alt TEP](/resources/tep_pnid.PNG)
<br>

## Dataset and Alarm Management
The IEEE dataset includes simulation results under normal steady-state and abnormal conditions, encompassing Active Root Cause and Normalization phases. While the normal simulation did not generate alarms, the abnormal conditions produced a significant number of alarm messages. The remaining portion of the work focused on alarm management techniques to reduce nuisance alarms.

## Text Dataset Structure
The dataset is organized into 3 CSV files, mirroring the original work:
- Original: Contains alarms from all 100 test cases without any alarm management techniques applied.
- Filtered: Includes alarms after implementing filtering techniques.
- Deadband: Contains alarms after implementing deadband techniques.

Each CSV file has 5 columns:
- **timestamp**: Timestamp of the alarm (start time and date are arbitrary and can be adjusted).
- **tag**: Name of the tag that triggered the alarm.
- **type**: Type of alarm, which can be one of the following 8 values (note that a tag can only have 1 type of alarm at any given time):
  * LL: Low Low alarm
  * L: Low alarm
  * H: High alarm
  * HH: High High alarm
  * LL NR/L NR/H NR/HH NR: Recovery messages for the respective alarms (e.g., when a Process Variable exceeds the Low alarm setpoint, the system generates an L NR message).
**description**: Description of the alarm as displayed on the operator's console.
**test**: Number of the test case from the original dataset (test cases are separated by 3-hour intervals).

## Potential Applications
This dataset can be valuable for research and development in various areas, including:
- Anomaly detection and fault diagnosis in ICS
- Development and evaluation of machine learning models for alarm analysis
- Evaluation of LLM models for industrial applications (embedding, summarization, questions answering)
 
# Reference:
- Gianluca Manca, November 1, 2020, ""Tennessee-Eastman-Process" Alarm Management Dataset", IEEE Dataport, doi: https://dx.doi.org/10.21227/326k-qr90.
- J.J. Downs and E.F. Vogel, “A plant-wide industrial process control problem,” Comput. Chem. Eng., vol. 17, no. 3, pp. 245–255, Mar. 1993, doi: 10.1016/0098-1354(93)80018-I.
- A. Bathelt, N. Lawrence Ricker and M. Jelali, “Revision of the Tennessee Eastman Process Model,”. IFAC-PapersOnLine, vol. 48, no. 8, pp. 309–314, Jun. 2015, doi: 10.1016/j.ifacol.2015.08.199.
- N.A. Adnan, “Performance Assessment and Systematic Design of Industrial Alarm Systems,” Ph.D. dissertation, Department of Electrical and Computer Engineering, University of Alberta, Edmonton, Alberta, Canada, 2013. Accessed: Dec. 4, 2020. [Online]. Available: https://era.library.ualberta.ca/items/2c7a4695-d97b-4f13-ab9e-6307bc12f7a0.
