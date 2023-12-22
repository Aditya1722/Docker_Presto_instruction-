rfifind -time 0.1 -xwin  -o Lband 20130925A_0001.fits 
prepdata -nobary -o Lband_topo_DM0.00 -dm 0.0 -mask Lband_rfifind.mask GBT_Lband_PSR.fil
realfft Lband_topo_DM0.00.dat
accelsearch -numharm 4 -zmax 0 Lband_topo_DM0.00.dat
Make a text file Lband.birds using - 
  gedit Lband.birds - add rfi you want to remove from DM = 0. exa,ple shown below  
  #freq   width #harm grow? bary?
  4.164   1.5    4    0      0 
  317.116 2      4    0      0

# Docker_Presto_instruction
* step 1 - pull the image from docker hub - `sudo docker pull adii1722/mwa_sps_pipeline:mwa`  
* step 2 - To start a docker container with name - mwa and effectively use GUI interation use this command  
  `sudo docker run -it --privileged --network host -e DISPLAY=:1 --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" --name mwa adii1722/mwa_sps_pipeline:mwa /bin/bash`  
  name of container = mwa
  name of repository = adii1722/mwa_sps_pipeline:mwa
* step 3 - After getting inside the container exit by typing exit and enter
* step 4 - start the container by using command - `sudo docker start mwa`
* step 4 - `sudo docker exec -it  mwa /bin/bash`
