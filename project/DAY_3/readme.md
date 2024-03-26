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