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
![D2_1](https://github.com/user-attachments/assets/41a3e16d-ef77-4f6f-a2f6-fd564f07fac5)

![D2_2](https://github.com/user-attachments/assets/3e3a726f-80b3-48b1-8316-feef517ad624)

![D2_3](https://github.com/user-attachments/assets/a9d35ee1-c6aa-4301-8c0f-5f54dd1c0a0b)

![D2_4](https://github.com/user-attachments/assets/2eb58a7b-1bb2-4249-a682-c75fd039bdcc)

Command to open magic 

```
magic -T /home/vsduser//Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

```

![D2_5](https://github.com/user-attachments/assets/ab533e6f-fbab-49d7-88ab-87bc4e86c956)

![D2_7](https://github.com/user-attachments/assets/dae853e8-9c88-4892-a73f-bf4fe04f1fa4)

## LAB SECTION - 2

Placement

```
run_placement

```

![D2_8](https://github.com/user-attachments/assets/8566ac9f-735c-4c5d-8a93-b850e028d0e3)

```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

```

Running Magic

![D2_9](https://github.com/user-attachments/assets/6d435bfa-3d8f-4c52-86eb-d9919959e8fc)

![D2_10](https://github.com/user-attachments/assets/7e7f35f5-909f-4e01-9bbe-4df7cdc5523e)


# SECTION-3 (LABS)

```
change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

enter command to clone github repo
git clone https://github.com/nickson-jose/vsdstdcelldesign

after cloning change directory
cd vsdstdcelldesign

copying the Magic tech file in vsdstdcelldesign
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech 

command to open custom inverter design in magic tool
magic -T sky130A.tech sky130_inv.mag &

```

