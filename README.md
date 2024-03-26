#Advanced-Physical-Design-Using-OpenLANE-Sky130

   --> Day_1 Inception of Open-Source EDA, OpenLANE & Sky130PDK
   ## Path to run the docker file
Desktop/work/tools/openlane_working_dir/openlane$ docker

![1](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/4bb4ecd0-bee2-45cb-b002-ba39b1a82cce)

![2](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/bf6ed14b-ad78-41e4-867a-71ac6eb096f6)

![VirtualBox_vsdworkshop_19_03_2024_16_09_12](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/8cd9565e-9de1-43ac-a2b2-66339ed0b63b)


OUTPUT-->
Total numbers of cells = 14876
numbers of D flip flop = 1613
so, flip flop ratio = no. of D ff / total no. cells = 1613 / 14876 = 0.108429



DAY_2  CHIP FLOOR PLANNING Using openlane

steps to run floorplan
![floorplan](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/47208a3b-2a43-45a8-b2a1-fed766866c48)

picorv32a file
![picorv32a floorplan](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/408bab35-a234-46e8-9fac-40780ba93f92)

ioPlacer file
![VirtualBox_vsdworkshop_18_03_2024_23_28_52](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/5bdf54c3-adf0-4605-a7d9-0127d66f5fc6)

If we want change anything in floorplan, we need to make changes in design related config file.
![placemt_magic2](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/3f55a087-223c-447e-804e-1427df1cc348)

![magic1](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/d12589d8-dde7-4edf-8d33-bf029d75c794)

![madic2](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/07f65736-bd3b-4593-b770-a273e9b07aa6)

![magic3](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/37da62de-9a63-44a5-99fb-e161445e73bc)


![magic](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/03d54a77-c654-419e-abf1-ec74f70e9e8c)


Library Binding and placement
![placement_amgic](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/73f4f89d-cf84-4db4-b332-ff3541b70355)
![placemt_magic1](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/bcaac299-54cc-4790-905c-abb594b1f725)

DAY_3 Labs for CMOS inverter ngspice simulations

Lab steps to git clone vsdstdcelldesign
To clone the gitlink the command used here is,
/Desktop/work/tools/openlane_working_dir/openlane$ git clone https://github.com/nickson-jose/vsdstdcelldesign.git
Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &

![inverter_3](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/97f60f85-12a9-4694-8ddf-2b83d8a172c3)

![inverter_1](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/259fd174-687f-43c9-86a5-12ab2d43b594)

![inverter_2](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/e3e0af70-7bb6-4150-b106-dc91f5b1a166)
![INverter_box](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/f16d7891-8e19-455e-9f05-0e78b324b0b6)


Spice extraction of CMOS inverter in magic tool.
![inverter_spice_1](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/9255e2a4-e46a-4164-9809-91a4fbe4dc4a)

   The final file of SPICE deck using Sky130 tech we can see below,
   ![313502671-597e0aa5-335c-4429-bb65-fcb0931e0553](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/c6ee759b-e68d-4348-b787-39556ddbe1ff)

  Command to directly load spice file for simulation to ngspice
     ngspice sky130_inv.spice
     ![inverter_output](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/be62bc23-d004-48f0-9172-07d70b78a602)
     ![inverter_top](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/cb1fe5b8-8ea9-4203-b636-4cbeb6595a70)
        
   pshort-->
     ![pshort](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/aa85d9b7-6cce-4c76-b422-5c67cc991bb7)

  Here we will calculate Rise time delay, Fall time delay and Propogation delay for the CMOS inverter output.
   ![inverter_cell_char](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/3819db0c-b8be-4c56-902e-9d2ebd44be61)


