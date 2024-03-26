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
   run_synthesis
   ![VirtualBox_vsdworkshop_26_03_2024_16_31_28](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/c0cd5177-60bb-4734-817e-18620c770c50)
   ![Screenshot 2024-03-19 110615](https://github.com/manishkumar754/VSDWorkshop/assets/132566236/fe652a08-18c4-43b3-a51e-44def563a6aa)
   The synthesis is Successful.

   


