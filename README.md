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
![D3_1](https://github.com/user-attachments/assets/85b1f683-78cc-47d2-874d-615d7896d175)

![D3_2](https://github.com/user-attachments/assets/70312ac9-72b9-4217-92a3-f029c85e9f54)

![D3_3](https://github.com/user-attachments/assets/20cb4b8e-6f51-443d-88dc-0a4f824e9603)

Difference between layout and lef

![D3_4](https://github.com/user-attachments/assets/e30fe1ef-4094-4a03-9c2d-5fb565400b21)

Commands to run in tkcon terminal of magic tool for spice extraction

```
command to check directory in which you are present
pwd

command to run for extraction of file to .ext format
extract all

command to enable parasitic Extraction
ext2spice cthresh 0 rthresh 0

command to convert ext to spice file format
ext2spice

```


![D3_5](https://github.com/user-attachments/assets/70372e0b-917f-4c50-8634-8a605a492aef)

![D3_6](https://github.com/user-attachments/assets/fa7f35f4-8e02-4532-bdf2-312995d4c2ff)

![D3_7](https://github.com/user-attachments/assets/6936a640-f29c-4936-b4d0-2fb8b9ab9855)

![D3_8](https://github.com/user-attachments/assets/4471f1e7-a788-44cb-8475-56175db7ead0)

![D3_9](https://github.com/user-attachments/assets/7588a085-8e92-461e-97a7-5a43f45687e6)

```
gedit sky130_inv.spice

```

```
ngspice sky130_inv.spice

```

![D3_10](https://github.com/user-attachments/assets/6d217052-fab9-445f-bb1a-e075052a7d87)

![D3_11](https://github.com/user-attachments/assets/16b4a59a-f646-4377-b1e0-0e43e7b21b7c)

![D3_12](https://github.com/user-attachments/assets/9f347242-4f3a-42ce-8742-140f400918a3)

![D3_13](https://github.com/user-attachments/assets/4ef07410-7cc9-4ef2-ab15-9600f86f0eb7)

```
//go to home directory
cd

//Command to download the lab files
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

//command to extract file
tar xfz drc_tests.tgz

// change directory to lab folder
cd drc_tests

//List all files and directories present in the current directory
ls -al

//Command to view .magicrc file
gvim .magicrc

//Command to open magic tool in better graphics
magic -d XR &

```


![D3_14](https://github.com/user-attachments/assets/bb1fa3d6-be75-4777-8b5d-14cf0ed063fd)

![D3_15](https://github.com/user-attachments/assets/59ebcff0-3577-49e6-988c-562ab74ba080)

![D3_16](https://github.com/user-attachments/assets/f445f365-46e5-42e9-9795-05e0d493c673)

# SECTION-4 (LABS)

Pre-layout timing analysis and Clock Tree Synthesis

```
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

```

```
magic -T sky130A.tech sky130_inv.mag &

```

In tkcon window

```
help grid

```

```
grid 0.46um 0.34um 0.23um 0.17um

```

![D4_1](https://github.com/user-attachments/assets/7a303212-5833-429f-82ea-147886efc85b)

![D4_2](https://github.com/user-attachments/assets/afc1b592-af53-4655-9c35-c3e73956dbb0)

![D4_3](https://github.com/user-attachments/assets/1c876cdd-9515-4b7f-906e-c497b17af1eb)

![D4_4](https://github.com/user-attachments/assets/a98fe7f0-8e47-4938-a348-78e4e57824af)

```
save sky130_vsdinv.mag

magic -T sky130A.tech sky130_vsdinv.mag &

lef write

cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

```

for lef file

```
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]

```


![D4_5](https://github.com/user-attachments/assets/9b507322-fbcf-44fb-a9f2-0bbb0e6436dd)

![D4_6](https://github.com/user-attachments/assets/f92b45bc-cdae-47da-ae42-9fe9f09ac020)

![D4_7](https://github.com/user-attachments/assets/a956ab09-bcf6-4aa1-a25e-eb20020c6b8b)

![D4_8](https://github.com/user-attachments/assets/bea47d94-7a86-4949-9920-164408672f36)

![D4_9](https://github.com/user-attachments/assets/d8b3bfa5-bcd9-49e6-b421-40c493c78118)

```
cd Desktop/work/tools/openlane_working_dir/openlane

docker

./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]

add_lefs -src $lefs

run_synthesis

```

![D4_10](https://github.com/user-attachments/assets/8fed508e-1e28-4d30-8f2b-a98258fa26bb)

![D4_11](https://github.com/user-attachments/assets/419f7287-5aab-4d20-82c3-9da620c52da6)

![D4_12](https://github.com/user-attachments/assets/3d596554-ad5b-4c71-b248-342f3f1efd24)

```
prep -design picorv32a -tag 16-10_13-08 -overwrite

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]

add_lefs -src $lefs

echo $::env(SYNTH_STRATEGY)

set ::env(SYNTH_STRATEGY) "DELAY 3"

echo $::env(SYNTH_BUFFERING)

echo $::env(SYNTH_SIZING)

set ::env(SYNTH_SIZING) 1

echo $::env(SYNTH_DRIVING_CELL)

run_synthesis

```


![D4_13](https://github.com/user-attachments/assets/67cf132e-97a0-4135-aed3-f0604f07525f)

![D4_13a](https://github.com/user-attachments/assets/01af192a-e8df-4f10-b6aa-d37267a8baee)

![D4_14](https://github.com/user-attachments/assets/70e53472-7c09-4ab1-ad5c-db62a5fb5a2c)

![D4_14a](https://github.com/user-attachments/assets/8d55d867-f138-4e75-8437-488e0d7b47ac)

![D4_15](https://github.com/user-attachments/assets/2df27964-6af4-449e-909a-831ba05804c8)




