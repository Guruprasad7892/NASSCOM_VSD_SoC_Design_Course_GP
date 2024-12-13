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

![D4_16](https://github.com/user-attachments/assets/8ee99463-494d-4920-a039-454b99b63e4b)

```
run_floorplan

init_floorplan

place_io

tap_decap_or

run_placement

```

![D4_17](https://github.com/user-attachments/assets/56ad6324-430a-497c-ae9f-9b1b7bcf7934)

![D4_18](https://github.com/user-attachments/assets/a9a14ea2-2f62-4108-845e-a475311a715a)

![D4_19](https://github.com/user-attachments/assets/f97a8936-8def-4181-b994-4aadbd75ea00)

![D4_20](https://github.com/user-attachments/assets/f39b5436-00ff-4ab1-90b5-fb223bf29159)

![D4_21](https://github.com/user-attachments/assets/dc192129-6bef-43e3-919e-bc5b624aed22)

```
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-10_13-08/results/placement/

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

```

![D4_22](https://github.com/user-attachments/assets/f64f0b76-96d2-484d-bfb1-224127494276)

![D4_23](https://github.com/user-attachments/assets/45459b1b-2bd8-4b72-98ad-df6b51a02d9e)

![D4_24](https://github.com/user-attachments/assets/7e94d3eb-4dd1-4c24-bc8e-4dd24d6dad69)

![D4_25](https://github.com/user-attachments/assets/9a4406d9-a95d-49b2-a32e-320a1cbf7c1f)

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

![D4_26](https://github.com/user-attachments/assets/892ceaeb-b74e-496c-a473-12150c36a897)

![D4_27](https://github.com/user-attachments/assets/a3b993eb-a157-450e-ae4a-784c2ed68f61)

![D4_28](https://github.com/user-attachments/assets/3fec7422-0c90-40ee-9912-99254288ba22)

```
cd Desktop/work/tools/openlane_working_dir/openlane

```


![D4_29](https://github.com/user-attachments/assets/79322008-43fe-40a2-9c19-30e4002926e6)

![D4_30](https://github.com/user-attachments/assets/cab5fc57-f8b0-4b10-9c39-b2dbba588a68)

```
help write_verilog

write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52/results/synthesis/picorv32a.synthesis.v

exit

```


![D4_31](https://github.com/user-attachments/assets/49fd89fe-2fe6-47cc-97a9-831da948da94)


```
//Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 11-10_06-41 -overwrite

//Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

//Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

//Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

//Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

//Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

//Now we are ready to run placement
run_placement

//Incase getting error
unset ::env(LIB_CTS)

//With placement done we are now ready to run CTS
run_cts

```

![D4_32](https://github.com/user-attachments/assets/6b20f1f0-837e-462b-9bf2-59173d3629b6)

![D4_33](https://github.com/user-attachments/assets/79ed8054-bb7c-4751-abe5-b9e9c19acaad)

![D4_34](https://github.com/user-attachments/assets/0bae5ca8-b3a5-4277-9e5b-296285d1d000)

![D4_35](https://github.com/user-attachments/assets/f2d36855-6d84-4046-858e-b8bd8f11619a)

![D4_36](https://github.com/user-attachments/assets/274e80b7-dfdf-44e3-9949-05c56d9f5f39)

```
//run OpenROAD tool
openroad

//Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef

//Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def

//Creating an OpenROAD database to work with
write_db pico_cts.db

//Loading the created database in OpenROAD
read_db pico_cts.db

//Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v

//Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

//Link design and library
link_design picorv32a

//Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

//Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

//Check syntax of 'report_checks' command
help report_checks

//Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

//Exit to OpenLANE flow
exit

```

![D4_37](https://github.com/user-attachments/assets/371a3417-f1bb-4940-8698-6523302c79cd)

![D4_38](https://github.com/user-attachments/assets/8e88b677-0451-4867-bdef-66779d4817bd)

![D4_39](https://github.com/user-attachments/assets/5bacc614-5065-4082-b331-c72eea8448a1)

![D4_40](https://github.com/user-attachments/assets/691458e8-8349-4478-bf7e-30c94c93caa5)

Commands to be run in OpenLANE flow to do OpenROAD timing analysis after changing CTS_CLK_BUFFER_LIST

```
//Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

//Removing 'sky130_fd_sc_hd__clkbuf_1' from the list
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

//Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

//Checking current value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

//Setting def as placement def
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/placement/picorv32a.placement.def

//Run CTS again
run_cts

//Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

//Command to run OpenROAD tool
openroad

//Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef

//Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def

//Creating an OpenROAD database to work with
write_db pico_cts1.db

//Loading the created database in OpenROAD
read_db pico_cts.db

//Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v

//Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

//Link design and library
link_design picorv32a

//Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

//Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

//Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

//Report hold skew
report_clock_skew -hold

//Report setup skew
report_clock_skew -setup

//Exit to OpenLANE flow
exit

//Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

//Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

//Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

```

![D4_41](https://github.com/user-attachments/assets/7b2d2a39-5948-41f9-8ce2-d8841be58e3c)

![D4_42](https://github.com/user-attachments/assets/8dfda166-e1fe-424b-ab1e-d9fce8d4a5f4)

![D4_43](https://github.com/user-attachments/assets/b311cc38-b1e2-446f-9d10-48a5b086d0ef)

# SECTION-5 (LABS)

Perform generation of Power Distribution Network (PDN) and explore the PDN layout.

```
//Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

//alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
//Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

```
```
to invoke the OpenLANE flow in the Interactive mode 
./flow.tcl -interactive

//command for packages need for openlane
package require openlane 0.9

//preparing the design for picorv32a
prep -design picorv32a

//Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

//set new value tfor synth size
set ::env(SYNTH_SIZING) 1

command to run synthesis
run_synthesis

# Following commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts

# Now that CTS is done we can do power distribution network
gen_pdn

```
![D5_1](https://github.com/user-attachments/assets/00f6b117-72f0-4ef6-b597-7e015d0f7fe9)

![D5_2](https://github.com/user-attachments/assets/06250b3c-8dee-4bc8-9e13-c57836e7adb0)

Commands to load PDN def in magic in another terminal

```
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-10_16-14/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &

```

567

Commands for routing

```
# Check value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Check value of 'ROUTING_STRATEGY'
echo $::env(ROUTING_STRATEGY)

# Command for detailed route using TritonRoute
run_routing

```

![D5_3](https://github.com/user-attachments/assets/0330d6fc-130e-48e7-9faf-e67a70a4f85f)

![D5_4](https://github.com/user-attachments/assets/c9d51a87-cab6-4ce9-860d-171fa444577b)


