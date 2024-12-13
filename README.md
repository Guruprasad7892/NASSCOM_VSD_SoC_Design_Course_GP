# NASSCOM_VSD_SoC_Design_Course_GP
# Open-source EDA, OpenLANE and Sky130 PDK
# SECTION-1 (LABS)
### Tasks to be Completed:-
### 1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
### 2. Calculating Flop_Ratio(D_flipflop)

### 1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
Invoking the OpenLANE_flow and Run synthesis

```
//Change directory to openlane flow directory
 cd Desktop/work/tools/openlane_working_dir/openlane

//alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e 
PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
//Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

```
```
//invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

//input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

//prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

//Now that the design is prepped and ready, we can run synthesis
run_synthesis

//Exit from OpenLANE flow
exit

//Exit from OpenLANE flow docker sub-system
exit

```
Screenshots of executed commands

![D1_1](https://github.com/user-attachments/assets/fa049502-6d18-400a-9668-fe74df927611)

![D1_2](https://github.com/user-attachments/assets/912534ef-7995-40d5-9b10-14fe18218590)

![D1_3](https://github.com/user-attachments/assets/8a350daf-401c-48ca-a149-6f99e53a939b)

### 2.Calculating Flop_Ratio(D_flipflop):-

![D1_4](https://github.com/user-attachments/assets/38cf4924-9894-41d8-9ce3-a990a43f7207)

![D1_5](https://github.com/user-attachments/assets/7766df61-f517-40d9-9dc8-38f5e97aeae5)

Number of D Flip Flop = 1613

Total number of cells = 18036

Calculating Flop ratio = no.of d-flipflop/total cells

```
Flop ratio = 1613/18036 = 0.0894

```
%of D Flip Flops in the area = 8.94%

# SECTION-2 (LABS)

## LAB SECTION - 1

Floor Planning

```
run_floorplan
```
