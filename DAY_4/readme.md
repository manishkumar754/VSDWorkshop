##Timing modelling using delay tables
Lab steps to convert magic layout to std cell LEF
  ![inverter_1](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/f89568f7-40de-4d5b-b9ee-9d4467ac2374)

Tracks These are using in the routing stage. These are nothing but metal layers.
  Go to this path We will get tracks info.
    vsduser@vsdsquadron:~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd$ less tracks.info
   ![track_info](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/6644be86-0f48-486e-83e7-9ace9b46d8e5)
 ![VirtualBox_vsdworkshop_26_03_2024_15_55_53](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/be1053b2-7829-42e2-a338-aa7ab7fdf8c9)
    
  help grid:-
 ![grid_dim](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/d44cd59b-504f-4300-a424-bb27d641bcf2)
 Now layout is done as per the pnr tool.
 Whenever we make the layout we just define the layers and contacts. we don't define the ports. Ports doesn't mean anything to the magic. 
 Ports are required while we want to extract the lef file. When we extract the lef file these ports are defined as pins.

 ![VirtualBox_vsdworkshop_26_03_2024_16_05_10](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/04929db3-58b8-4795-a734-be3ffd437e57)

 We will see the file in vsdstdcelldesign folder.
 <img width="764" alt="image" src="https://github.com/manishkumar754/VSDWorkshop/assets/132566236/d01915f7-d455-405a-af1e-7d5a8a60ef6f">
![VirtualBox_vsdworkshop_26_03_2024_16_12_04](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/c297f25a-7aa9-4920-b3b1-6b6f6f066e7e)

sky130_vsdinv.lef file
  ![VirtualBox_vsdworkshop_26_03_2024_16_12_38](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/209486d5-b160-4e79-9481-1f19071d9a75)
sky130_fd_sc_hd_typical.lib file 
 ![VirtualBox_vsdworkshop_26_03_2024_16_18_53](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/2440be26-f7b0-4ca7-b68d-822b4d677bbb)

Before going to run synthesis, we have modify config file.
<img width="759" alt="image" src="https://github.com/manishkumar754/VSDWorkshop/assets/132566236/21fc62e9-762c-4534-ac06-ed93e44ca977">
 
 ![Screenshot 2024-03-19 110404](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/dd4afb25-305b-4579-8d90-55c30f5aa468)

 Package :-
 ![VirtualBox_vsdworkshop_26_03_2024_16_18_53](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/f08eba1d-5ab4-4f69-9816-dc5012ad4515)
 Design Prepration:- 
 ![VirtualBox_vsdworkshop_26_03_2024_16_25_01](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/0cbf8c32-52e9-4d0b-b68b-dcdebdfee9ce)

 RUN SYNTHESIS:- 
     
       run_synthesis :-
   ![VirtualBox_vsdworkshop_26_03_2024_16_31_28](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/c0cd5177-60bb-4734-817e-18620c770c50)
   ![Screenshot 2024-03-19 110615](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/fe652a08-18c4-43b3-a51e-44def563a6aa)
  
   The synthesis is Successful.


  ## Lab steps to configure synthesis settings to fix slack and include vsdinv
  1. Go to README.md. to see any stratergies to overcome timing violations.
     -->wns Worst neagative slack -->tns total negative slack.
     <img width="737" alt="image" src="https://github.com/manishkumar754/VSDWorkshop/assets/132566236/61653191-5b33-42d9-acd2-4ac7d952dd3e">
     <img width="684" alt="image" src="https://github.com/manishkumar754/VSDWorkshop/assets/132566236/c14c1c5b-b325-4a92-bd58-f3fb1ea1bea5">

 After set the SYNTH_STRATEGY & SYNTH_SIZING As we expected the area increased.
The steps I followed is

  1. Go to openlane directory type docker.
  2.  pwd
  3.  ls-ltr
  4.  ./flow.tcl -interactive
  5.  package require openlane 0.9
  6.  prep -design picorv32a -tag run1 -overwrite
  7.  set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
  8.  add_lefs -src $lefs
  9.  run_synthesis ---> Here I got some tns & wns values and some area. By using area and sizing strategy i increased area and decreased the dealy (tns &wns values)
  10.  prep -design picorv32a -tag 22-03_17-07 -overwrite
  11.  set lefs [glob $::env(DESIGN_DRV)/src/*.lef]
  12.  add_lefs -src $lefs
  13.  set ::env(SYNTH_STRATEGY) "DELAY 1"
  14.  set ::env(SYNTH_SIZING)
  15.  run_synthesis
 

  Area increased to --> Chip area for module '\picorv32a': 196832.528000
   
    tns &wns became 0
  ![Screenshot 2024-03-22 133842](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/fe12b286-3936-4e03-83ff-e6cc68fc718b)

  Locating the Custom Inverter Cell in Layout

  After Placement stage we can see new inverter cell Which is invoked intentionally is placed in the design.

  steps
   Search for instance of cell sky130_myinverter inside the DEF file after placement stage:
   cat picorv32.def | grep sky130_vsdinv: Open the def file via magic:
   magic -T /home/vsduser/Desktop/OpenLane/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.nom.lef def read picorv32.def &

  ![Screenshot 2024-03-23 153423](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/a40d3ccd-05ae-4fc4-adbd-cb30ba257480)
  ![VirtualBox_vsdworkshop_26_03_2024_09_50_09](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/7c026bb1-3eeb-4ad2-8598-79ef092d53f1)
  ![Screenshot 2024-03-22 135109](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/84db23ee-3eab-439a-b217-4cdf7b51d6ff)

 
 ## Clock-tree Synthesis

  ![Screenshot 2024-03-23 211238](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/756ec7ab-a3ec-4302-b78c-8c0af2771c58)
  
  ![Screenshot 2024-03-23 211459](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/0ed0e4af-34cd-4473-a970-ba47a6fea0e6)

  Post Clock tree synthesis
  We invoke openroad in the openlane flow
 
    %openroad
 Run the following commands to create a .db file which the openroad software can read


     read_lef /openLANE_flow/designs/picorv32a/runs/run1/tmp/merged.lef
     read_def /openLANE_flow/designs/picorv32a/runs/run1/results/cts/picorv32a.cts.def
     write_db pico_cts.db
     read_db pico_cts.db
     read_verilog /openLANE_flow/designs/picorv32a/runs/21-03_02-34/results/synthesis/picorv32a.synthesis_cts.v
     read_liberty $::env(LIB_TYPICAL)
     link_design picorv32a
     read_sdc /openLANE_flow/designs/picorv32a/src/picorv32a.sdc
     set_propagated_clock [all_clocks]
     report_checks -path_delay min_max -fields {slew trans net cap input_pin} -format full_clock_expanded -digits 4


   Replace the clock buffer by giving the following command
   
      set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

   We observe the output as
    
       sky130_fd_sc_hd__clkbuf_2 sky130_fd_sc_hd__clkbuf_4 sky130_fd_sc_hd__clkbuf_8

  ![Screenshot 2024-03-24 120232](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/4daaffc4-e39b-492b-b430-353ef43d0d6d)
 
   ![Screenshot 2024-03-24 120653](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/c147d16f-b652-42c7-a7b9-857b55fae087)

   //Layout after CTS
    ![Screenshot 2024-03-24 122603](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/1f4d3d2f-bd0a-4081-aa10-2f9ec4c8fd9c)






