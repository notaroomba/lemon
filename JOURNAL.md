# 10/2/2026 8 PM - Planning

_Time spent: 5h_

I wanna make a pathfinder scooter like lime but it COMES ADN FINDS ME.

Requirements:

- Self driving
- Electric
- 60 km/h top speed
- 30 km range
- Locks and

I started planning the electric scooter and yea. So I weigh around 50 kg and then doing some fancy math I would need around 100N\*m motor to move 100kg of weight (including apssenger and scooter). I think this is reasonable.

I LEARNED ABOUT HUB MOTORS ADN THEYRE SO COOL

https://www.amazon.com/Direct-Drive-Orientation-Integrated-4096-Line-Encoder/dp/B0GR5J5ZSY
https://www.aliexpress.us/item/3256812676876775.html?
https://www.amazon.com/Electric-Scooter-Replacement-Accessories-Installation/dp/B0DSLGZ2XB

WHEEL:
https://www.aliexpress.us/item/3256805371324103.html

https://ae-pic-a1.aliexpress-media.com/kf/Sf441648b5ffa4cfdb1451541820772744.pdf?spm=a2g0o.detail.0.0.260ahA4jhA4jFv&file=Sf441648b5ffa4cfdb1451541820772744.pdf

Lidar https://www.aliexpress.us/item/3256812379299784.html - 12m
https://www.aliexpress.us/item/3256803429491386.html SLAMTEC LIDAR S3 or S2 - 40m

Brake: https://www.aliexpress.us/item/3256808605416645.html
but buy brake wheel after sizing motor or makign custom brake wheel

Charger: https://www.amazon.com/Dell-Adapter-Delivery-Connector-6-4x3-1x0-9/dp/B0FN5MFYH1

custom esc

Batteries:
16S8P 21700

TPS26750 - USB C 240W
LT8490 - Battery Charging
BQ76952 - Measure, balance, primary protection
BQ77216 - Backup overvoltage protection

ts is like peak and I want to use some for a self driving scooter.

I want to do a thing where I have teh batteries, then it connects to the BMS adn then that gets connected to a fust adn then a switch to turn on and or off the scooter. Then from there there are 2 dual (positive and negative) wires that go to a rear controller adn then the front controller.

# 10/3/2026 4 PM - Planning

_Time spent: 4h_

So after looking through parts I also wanted to make the battery swapable but I decided to do this on a later version because yes.

For this I would have like a rail in the bottom of the scooter adn it would just slide in and out. I would have a locking mechanism to keep it in place and then a quick connect for the battery terminals. This way, when the battery is low, I can just swap it out for a fully charged one without having to wait for it to charge.

actually after thinking about it I want to go all in and make it modular so that means also thinking abotu the connector adn how I am going to do it. I want to ake it so that I can take the battery out adn that it has 4 connectors, 2 for power and 2 for data. This way, I can have a battery pack that has its own BMS and can communicate with the scooter's main controller. This will also allow me to have different battery packs with different capacities and chemistries.

# 10/4/2026 8 PM - Planning

_Time spent: 5h_

Ok after some more planning and talking with claude, I want it to be able to drive itself and that means doing something with LiDAR and cameras. I want to have a LiDAR on the front of the scooter that can detect obstacles and map the environment.

I realisticaly can't build the lidar myself or the camera sys
https://www.firefly.store/products/roc-rk3588s-pc-8-core-8k-ai-mainboard
or
https://www.amazon.com/dp/B0BZJTQ5YP

but realistically I want to use the jetson along with the lidar

ACTUALLY NEVERMIND

I just want to make the scooter first adn then ill add in the fancy stuff later. I want to make sure that the scooter is functional and safe before adding in the self-driving features.

so now I have some things to do

- CAD Battery pack and frame
  - Cad 1S holder adn then scale up to 16S
  - cad an aluminum frame that has a port
- Make battery board (inside the pack)
  - BQ76952: measure, balance, primary protection
  - BQ77216: backup overvoltage protection
  - Discharge switch, precharge, swap connector
- Make charger board (inside the pack)
  - STM32G0B1 + ESP32
  - LT8490: charge regulation
  - TPS26750: 240 W USB-C input (HX-TYPE-C 16P IPX7-A-L8.15 as its waterproof)
  - XT Connector (C428722)
- Make custom ESC/Motor Controller (build two)
  - STM32F405
  - 16S input, 100 V rated parts
  - 50 A battery peak, 120 A phase peak
  - FOC with halls, regen, CAN
- Make central board
  - STM32G0B1:
    - CAN, GPS, LoRa, enable line
  - ESP32:
    - WiFi, BLE, OTA
- Make frame with battery dock
