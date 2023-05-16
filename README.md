Here is everything I used to convert our Makerbot Replicator to a fairly capable klipper machine with a heated bed and input shaper.

I heavily used Rolohaun's makerbot replicator 5th gen parts for this, but I had to change some things for this specific printer. https://github.com/rolohaun/Replicator5-Klipper

This build uses M3 M2.5 and M2 screws, I used socket head ones, but any should be fine. Just be careful not to split the parts if you use countersunk screws. You'll need to source a good amount of M3 screws from M3x6 to M3x50. a regular M2.5 and M2 kit should cover those fine.

Some items may not work as intended, I've never done this before so let me know if something isn't working. The screen mount will probably not work as it is at the moment, but some post processing got it there for me.

I've included my toolhead STEP file, hopefully it can prove useful if anyone needs to make any changes.

I will comment out everything from the configs that won't run on an initial klipper setup, so make sure to uncomment these as you install ADXL support and so on.

I mounted the raspberry pi to where the old screen PCB and other bits were located. Use the original face plate piece and just replace the metal bracket with the printed one. You may have to cut some holes into the face plate sides to achieve enough room for the pi. I couldn't fit a power plug in there, so I soldered a ground wire to the usb housing chasis and stuck power across the two front GPIO pinsto save space. I hotglued the original encoder wheel back in place, but this is completely optional. The several usb,ethernet, and ADXL wires can be run along the top of the motion system where the original HMDI cord was set, there is enough room where they don't get pinched, but be careful because it's very easy for a wire to move into a location where it will get pinched. (Make sure to wire the original ground from the motion system frame into a common ground(also a good idea to do this with the PSU body))

The SKR Mini e3 v3 and Meanwell 350 PSU go in fairly simple, you'll need to have the entire machine apart for this, but you should already be there from taking the old parts out. Run the mainboard power wires around the same way the stock ones were run (under and in front of the Z platform). I cut a hole in the back panel and wired up a standard plug socket as well as an ethernet wall port and a plug for the Rpi power. this isn't difficult as theres plenty of room, but it can be a pain to get through that thick metal unless you have sufficient tools. The mainboard mount and the mainboard fan mount will sandwich the SKR mini together, but it can be easier to install the board on the mounting plate first with 1 or 2 of the thumbscrews, and then put the fans on with screws from the bottom. Make sure to only put the thumbscrews on the mounting point NOT used by the fan mounts.

The toolhead is a bit complex, it's probably easiest to assemble most of it outside the printer with the mainboard side wires disconnected. Use the dragonfly spacer and screw down the hotend (pretty much everything should use threaded inserts here). Now you can use the 4010 blower fans to hold the back and front hotend halves together (don't put any screws in the front top holes for the fan yet). Now is a good time to put the inserts for the LDO orbiter in place, and screw that down (the PTFE tube can be tricky to cut to length). Now screw the Toolhead mounting plate with 3 M3 screws along with the bltouch bracket to the back of the hotend assembly (the cables should be able to route through this part) You can then put the 4010 axial fan into the Front hotend part along with the fan grill and route the cable through one of the top holes (you'll need to cut the connector off if it has one).Next you'll go over to the metal plate that attaches the two rail carriages together on the printer, and just take out the 4 screws on the bottom vertical part. Then you'll mount the "Rail-Fan Mount" and screw that down. Then stick two M3x45-50 screws into the front two holes of that, followed by 3 washers on each one after they're pushed in. Now you can take the toolhead assembly and push it over the two long screws coming from the rail mount and it should hold everything in place. Don't full tighten this down yet, but instead put the Toolhead mounting spacer in place where it will screw into the original toolhead mounting holes (3 M3 holes). Now tighten everything in place and the toolhead should be good.

The cable guide just VHB tapes to the open rectangle shaped hole towards the back of the machine, this is covering the spot where the old spool holder was. That is completely useless to us now, so we'll cover it up with this. This can be added or removed after the hotend is already wired and tied up.

The side mounted spool holder is not my design, if I can find the original one I will link it in here, but there have been a couple options i've seen. I had to mirror this one so it would sit on the right side of the machine, but anything you can get to work will do the trick really.

The neopixels are completely optional, the wiring kinda sucks because the data needs to go directionally, while the power is best supplied directly. This machine has a lot of open space to mount these though, so get creative if you feel like it.

I did not set out to make this a cheap as can be upgrade, nor did I spend extra time making it easier than necessary. It should work as it is and it should be a reliable enough machine I would hope. (not much time on mine yet)

BOM:

SKR Mini e3 v3 (I just used this one because i've used it before and it's easy to setup for me)
https://www.amazon.com/BIGTREETECH-Control-TMC2209-Stepper-Upgrade/dp/B09LC34SCK/ref=sr_1_3?keywords=skr+mini+e3+v3&qid=1678119759&sr=8-3

Dragonfly BMS (you'll need to adjust some stuff to fit a different hotend)
https://www.amazon.com/Dragon-Printer-Compatible-Extruder-Creality/dp/B08MF9NPMT/ref=sr_1_1_sspa?crid=1O1NJGBAL1LXB&keywords=dragonfly+hotend&qid=1678119775&sprefix=dragonfly+hotend%2Caps%2C89&sr=8-1-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUEyU0dVUlBPMTMyMUVRJmVuY3J5cHRlZElkPUEwNjA5Njc2OUQyOFlBNUhNWTNBJmVuY3J5cHRlZEFkSWQ9QTA5MzM2NTQyUVhQNUVWTkE4UU9SJndpZGdldE5hbWU9c3BfYXRmJmFjdGlvbj1jbGlja1JlZGlyZWN0JmRvTm90TG9nQ2xpY2s9dHJ1ZQ==

24v 60w Heater cartidge (interchangeable with any regular heater cartidge)
https://www.amazon.com/24V-60W-Temperature-Cartridge-Extruder/dp/B08CNCHC29/ref=sxin_16_pa_sp_search_thematic_sspa?content-id=amzn1.sym.8f2f40b3-26c0-4f88-be94-372390ff23da%3Aamzn1.sym.8f2f40b3-26c0-4f88-be94-372390ff23da&crid=3LM1BKTJAS8NG&cv_ct_cx=e3d+heater+cartridge+24v&keywords=e3d+heater+cartridge+24v&pd_rd_i=B08CNCHC29&pd_rd_r=3350750d-3d3d-46b7-b900-1e6f681887fc&pd_rd_w=jbDcy&pd_rd_wg=yeRlB&pf_rd_p=8f2f40b3-26c0-4f88-be94-372390ff23da&pf_rd_r=J2M3RWS96ME8FTFNKJ76&qid=1678824700&sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D&sprefix=e3d+heat%2Caps%2C178&sr=1-2-364cf978-ce2a-480a-9bb0-bdb96faa0f61-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUEzRlU1WkRTVDlHWVBQJmVuY3J5cHRlZElkPUEwMjA5NDk3Mzc0MDcwOTBBNlNaRyZlbmNyeXB0ZWRBZElkPUEwNzAxMzQ0WFFWRkNJTllHV0Q2JndpZGdldE5hbWU9c3Bfc2VhcmNoX3RoZW1hdGljJmFjdGlvbj1jbGlja1JlZGlyZWN0JmRvTm90TG9nQ2xpY2s9dHJ1ZQ==

Thermistor x2 (bed and hotend)
https://www.amazon.com/HT-NTC100K-Thermistor-Creality-Compatible-Ender-3-5/dp/B09WDR1M5Q/ref=sr_1_7?crid=1DBYHQZ5ZI5C7&keywords=e3d+thermistor&qid=1678824740&s=industrial&sprefix=e3d+therminstor%2Cindustrial%2C85&sr=1-7

4010 Axial fans x3
https://www.amazon.com/WINSINN-Ender-Upgrade-Bearing-CR-10S/dp/B08R9L9YR2/ref=sr_1_3?crid=1AXTKNAK10I54&keywords=4010+fan+24v&qid=1678824836&sprefix=4010%2Caps%2C128&sr=8-3

4010 Blower fans x2
https://www.amazon.com/WINSINN-Blower-Upgrade-Bearing-CR-10S/dp/B08R9J189W/ref=sr_1_2?crid=G8PXRL4591HR&keywords=4010+blower+fan+24v&qid=1678824857&sprefix=4010+blower%2Caps%2C115&sr=8-2

BLTouch Probe (feel free to fit a limit switch to this somehow)
https://www.amazon.com/Creality-Upgraded-BLTouch-Leveling-Mainboard/dp/B08MD3ZJTD/ref=sr_1_4?crid=28WDXN5NYAZT&keywords=bltouch&qid=1678825509&sprefix=bltouch%2Caps%2C85&sr=8-4

Meanwell LRS 350 (I chose this because I know it can handle everything it needs to, and I like to go with reputible PSUs)
https://www.amazon.com/MEAN-WELL-LRS-350-24-Switching-Printer/dp/B07SQLJG5L/ref=sr_1_1_sspa?gclid=CjwKCAjw_MqgBhAGEiwAnYOAei2VWbKdvsSdyooPUN5TzMSZBUCXdxkqRbfCErFEm9ykh8cDXO_G9xoCBi8QAvD_BwE&hvadid=580990752887&hvdev=c&hvlocphy=9004590&hvnetw=g&hvqmt=e&hvrand=13940442688755730374&hvtargid=kwd-296267630854&hydadcr=946_1014986914&keywords=lrs-350-24&qid=1678992967&sr=8-1-spons&psc=1&smid=A28HQ7WE3N597P&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUFDTTRKWjA3UUpUOUcmZW5jcnlwdGVkSWQ9QTA4ODUyMzgzMVZPTDRKRTE5NjE4JmVuY3J5cHRlZEFkSWQ9QTA1NjYzNjUxNVE5SDVaVDdGNkRGJndpZGdldE5hbWU9c3BfYXRmJmFjdGlvbj1jbGlja1JlZGlyZWN0JmRvTm90TG9nQ2xpY2s9dHJ1ZQ==

Power socket and switch
https://www.amazon.com/FILSHU-Socket-Module-Wiringiec320-illuminated/dp/B08L2522DF/ref=sr_1_2?crid=95ZHNLQ0QAJB&keywords=10A250v+switch+power+socket&qid=1679066143&s=hi&sprefix=10a250v+switch+power+socket%2Ctools%2C72&sr=1-2

Ethernet Ports x1
https://www.amazon.com/VICTEK-Female-Keystone-Couplers-White/dp/B01JJ46JX4/ref=sr_1_1_sspa?crid=2K333Q9H4LNK4&keywords=ethernet+keystone&qid=1679066534&sprefix=ethernet+keystone+%2Caps%2C88&sr=8-1-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUExMUNESUlKSVg4ME0wJmVuY3J5cHRlZElkPUEwNzg1NTcyM0Q2RDAyVzhCSUFGUiZlbmNyeXB0ZWRBZElkPUEwMDEzNjE5MU85VVZBSEtWRllXSSZ3aWRnZXROYW1lPXNwX2F0ZiZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU=

PET Expandable cable sleeving
https://www.amazon.com/PET-Expandable-Sleeving-PureBlack-BlackRed/dp/B081MRG8BT/ref=sxin_16_pa_sp_search_thematic_sspa?content-id=amzn1.sym.8f2f40b3-26c0-4f88-be94-372390ff23da%3Aamzn1.sym.8f2f40b3-26c0-4f88-be94-372390ff23da&crid=W3M872H6D350&cv_ct_cx=braided%2Bwire%2Bloom&keywords=braided%2Bwire%2Bloom&pd_rd_i=B081MRG8BT&pd_rd_r=9ace31f1-ab59-4cb0-b51a-99bb6971f01d&pd_rd_w=7eNPX&pd_rd_wg=Zrd5v&pf_rd_p=8f2f40b3-26c0-4f88-be94-372390ff23da&pf_rd_r=EB1WVVV2AGQSB4Z7DJXW&qid=1679066577&sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D&sprefix=braided%2Bwire%2Bloom%2Caps%2C99&sr=1-3-364cf978-ce2a-480a-9bb0-bdb96faa0f61-spons&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUEyM0lQR0JUQTdORldPJmVuY3J5cHRlZElkPUEwNzAwNTYxM0JYV0NHSlpNRzE1WiZlbmNyeXB0ZWRBZElkPUExMDI0NjQwMVlCTVBWSzRURlZORiZ3aWRnZXROYW1lPXNwX3NlYXJjaF90aGVtYXRpYyZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU&th=1

USB A to female USB A Cable (can be used to connect pi to mainboard)
https://www.amazon.com/Sabrent-22AWG-Extension-Cable-Female/dp/B019DZG9DY/ref=sr_1_4?crid=RSBCAXD4J56O&keywords=usb+3.0+to+female+usb+6ft&qid=1679073813&sprefix=usb+3.0+to+female+usb+6ft%2Caps%2C94&sr=8-4

Silicone heater pad 200x150 24v (will need to tape on thermistor)
https://www.aliexpress.us/item/2255800268049970.html?spm=a2g0o.productlist.main.1.6fa83891FsiRjp&algo_pvid=0eee9bb8-e024-461c-896d-1feed1d5d96f&aem_p4p_detail=202304061437434440692269447040002160150&algo_exp_id=0eee9bb8-e024-461c-896d-1feed1d5d96f-0&pdp_npi=3%40dis%21USD%2120.67%2119.64%21%21%21%21%21%4021021aa216808170633033797d06d3%2110000003741606365%21sea%21US%210&curPageLogUid=fhW2VxF5hPQk&ad_pvid=202304061437434440692269447040002160150_1&ad_pvid=202304061437434440692269447040002160150_1 200x150 24v

Die Springs 18x20mm x3 (used for bed)
https://www.amazon.com/uxcell-Printer-Stamping-Compression-Electric/dp/B0BVKDT67R/ref=sr_1_2_sspa?crid=3383XFDCC473P&keywords=18mm%2Bod%2Bspring&qid=1680819172&sprefix=18mm%2Bod%2Bspring%2Caps%2C95&sr=8-2-spons&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUEzS0NKM05OSzNFUU43JmVuY3J5cHRlZElkPUEwNjc1OTM2SzNEVTlCOU9LT1E1JmVuY3J5cHRlZEFkSWQ9QTA1MzIxNzUxVkI5ODJIVDM3QlRJJndpZGdldE5hbWU9c3BfYXRmJmFjdGlvbj1jbGlja1JlZGlyZWN0JmRvTm90TG9nQ2xpY2s9dHJ1ZQ&th=1 18x20mm x4

M6 Screw assortment (M6x25-30 should work, but untested (used for bed))
https://www.amazon.com/Cicidorai-Stainless-Assortment-Machine-Threads/dp/B08Z7BW2XG/ref=sxin_16_pa_sp_search_thematic_sspa?content-id=amzn1.sym.c8697a08-4071-4b95-a6c6-18057bcdb898%3Aamzn1.sym.c8697a08-4071-4b95-a6c6-18057bcdb898&cv_ct_cx=m6x35+screw&keywords=m6x35+screw&pd_rd_i=B08Z7BW2XG&pd_rd_r=97ba164e-7b6b-4eea-a615-6e634bc5f07d&pd_rd_w=Ld01y&pd_rd_wg=bzPQx&pf_rd_p=c8697a08-4071-4b95-a6c6-18057bcdb898&pf_rd_r=D5TT7G9Y7MHVCRVWCA1H&qid=1680820620&s=industrial&sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D&sr=1-5-364cf978-ce2a-480a-9bb0-bdb96faa0f61-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUExOUJIS0pSUkcySVhYJmVuY3J5cHRlZElkPUEwMDY5OTQ4WFZGREJWRDlTODcyJmVuY3J5cHRlZEFkSWQ9QTAzNTkzMDlBVEM3MlhYTjRFQ0smd2lkZ2V0TmFtZT1zcF9zZWFyY2hfdGhlbWF0aWMmYWN0aW9uPWNsaWNrUmVkaXJlY3QmZG9Ob3RMb2dDbGljaz10cnVl

Springsteel PEI buildplate 200x300mm
https://www.aliexpress.us/item/2255800124796619.html?gatewayAdapt=glo2usa4itemAdapt&_randl_shipto=US 200x300mm

LDO Orbiter extruder
https://www.printedsolid.com/products/ldo-orbiter-v2-dual-drive-direct-extruder?pr_prod_strat=use_description&pr_rec_id=c798ca84b&pr_rec_pid=6664099692629&pr_ref_pid=6817414021205&pr_seq=uniform

Heatshrink solder connectors (completely optional)
https://www.amazon.com/Connectors-Sopoby-Waterproof-Electrical-Automotive/dp/B0BKSJQC9Q/ref=sr_1_3?crid=LL1SFJ09DTYX&keywords=heat+shrink+solder+connectors&qid=1681410996&sprefix=heatshrink+solder%2Caps%2C154&sr=8-3

Stepper Motors x2 (optional)
https://www.amazon.com/STEPPERONLINE-Stepper-63-74oz-Connector-Extruder/dp/B07LCK19D5/ref=sr_1_4?crid=3TT46KK0S5NOR&keywords=nema%2B17%2Bstepper%2Bmotor&qid=1681937921&sprefix=nema%2B17%2Caps%2C143&sr=8-4&th=1

PiTFT43
https://www.amazon.com/BIGTREETECH-Raspberry-Controller-Capacitive-105-5X67mm/dp/B09791ZG1B

RPi Ribibon cables
https://www.amazon.com/Arducam-Raspberry-Camera-Ribbon-Extension/dp/B07SM6JTTM/ref=sr_1_2_sspa?crid=1UAD73DRXUCFO&keywords=raspberry+pi+display+cable&qid=1683749530&sprefix=raspberry+pi+display+cable%2Caps%2C92&sr=8-2-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUExQTFTREk0Ulk5ODBDJmVuY3J5cHRlZElkPUEwNTM3ODc4MTNTTThDQjRPWjc4NSZlbmNyeXB0ZWRBZElkPUEwMjE5MjQwMTJOMlMwUUM1TDQ1OSZ3aWRnZXROYW1lPXNwX2F0ZiZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU=

PTFE Tubing
https://www.amazon.com/Teflon-tubing-Filament-Printer-Tech/dp/B073RDFTDV/ref=sr_1_2_sspa?crid=ODTQ5FW67HQM&keywords=ptfe%2Btube%2Bfor%2B1.75mm%2Bfilament&qid=1683749659&refinements=p_72%3A1248921011&rnid=1248919011&s=industrial&sprefix=ptfe%2Caps%2C178&sr=1-2-spons&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUExS1ROTElIM1BZQ1dVJmVuY3J5cHRlZElkPUEwMjY5NzI0MVNQSEs3S0Q2U09FUyZlbmNyeXB0ZWRBZElkPUEwMDQ1OTA2MlhDTTUyTUpLMTROVyZ3aWRnZXROYW1lPXNwX2F0ZiZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU&th=1

Heatset Inserts
https://www.amazon.com/EEEEE-Threaded-Assortment-Printing-Injection/dp/B0B47MZ1SG/ref=sr_1_1_sspa?crid=9RDYTKVYLZVU&keywords=threaded%2Binserts&qid=1684185645&s=industrial&sprefix=thread%2Cindustrial%2C109&sr=1-1-spons&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUEyVjlWTEhGNFBKSjQ3JmVuY3J5cHRlZElkPUEwNjEwMTg5MTRQTzYzVVQxME5OWSZlbmNyeXB0ZWRBZElkPUEwMzQwNzU4MllHOTIxS080V1Y2UiZ3aWRnZXROYW1lPXNwX2F0ZiZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU&th=1