# Industrial Control System (ICS) Alarm Text Dataset - Based on Tennessee Eastman Process
This repository provides a textual dataset of Industrial Control System (ICS) alarms, derived from the "Tennessee-Eastman-Process" Alarm Management Dataset by Gianluca Manca (2020): "Tennessee-Eastman-Process" Alarm Management Dataset, IEEE Dataport.

## Origin and Process Description
The Tennessee Eastman Process (TEP) is a widely used simulation model of a chemical plant, originally developed by Downs and Vogel in 1993. It serves as a realistic platform for researchers and engineers to test and benchmark control strategies, fault detection methods, and process monitoring techniques. The TEP simulates a complex chemical process involving five major units: a reactor, a condenser, a compressor, a separator, and a stripper. These units work together to convert four gaseous reactants (A, C, D, and E) into two liquid products (G and H).

The model's complexity and realistic behavior have made it a valuable tool in the field of process control and related research areas. Several researchers have contributed to its refinement and analysis, notably A. Bathelt, N. Lawrence Ricker, and M. Jelali in their work "Revision of the Tennessee Eastman Process Model" and E. Arroyo in "Capturing and Exploiting Plant Topology and Process Information as a Basis to Support Engineering and Operational Activities in Process Plants."

Key Components of the TEP:
- **Reactor**: The heart of the process where the gaseous reactants (A, C, D, and E) undergo a chemical reaction to produce the desired liquid products (G and H) along with a byproduct (F).
- **Condenser**: This unit cools down the gaseous product stream exiting the reactor, causing some components to condense into a liquid state.
- **Separator**: The cooled product stream enters the separator, where it is separated into its gaseous and liquid components.
- **Compressor**: The gas stream from the separator, containing unreacted reactants and byproduct, is recycled back into the reactor by the compressor.
- **Stripper**: The liquid stream from the separator goes to the stripper, where the final products (G and H) are separated from any remaining unreacted components and byproduct.

<br>

![alt TEP Process](/resources/tep_pnid.PNG)

<br>

## Dataset and Alarm Management
The IEEE dataset includes simulation results under normal steady-state and abnormal conditions, encompassing Active Root Cause and Normalization phases. While the normal simulation did not generate alarms, the abnormal conditions produced a significant number of alarm messages. The remaining portion of the work focused on alarm management techniques to reduce nuisance alarms.

## Text Dataset Structure
The dataset is organized into 3 categories, mirroring the original work:
- Original: Contains alarms without any alarm management techniques applied.
- Filtered: Includes alarms after implementing filtering techniques.
- Deadband: Contains alarms after implementing deadband techniques.

As you can see, the proposed alarm management techniques reduced the total number of alarms by 90%. Using a deadband further reduced alarms by an additional 80%.

Each CSV file has 4 columns:
- **timestamp**: Timestamp of the alarm (start time and date are arbitrary and can be adjusted).
- **tag**: Name of the tag that triggered the alarm.
- **type**: Type of alarm, which can be one of the following 8 values (note that a tag can only have 1 type of alarm at any given time):
  * LL: Low Low alarm
  * L: Low alarm
  * H: High alarm
  * HH: High High alarm
  * LL NR/L NR/H NR/HH NR: Recovery messages for the respective alarms (e.g., when a Process Variable exceeds the Low alarm setpoint, the system generates an L NR message).
- **description**: Description of the alarm as displayed on the operator's console.

This dataset, while not encompassing the full range of alarms seen in modern control systems, offers a practical representation of real-time industrial processes, enabling the testing and refinement of tools and approaches before deployment in production environments.

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
