# Affordable Augmented Reality Research Platform (AARRP) intro
Welcome to this page for the AARRP project.
This page and its content is intended as a tutorial and building guide for researchers and AR-enthusiast to build their own affordable augmented reality research platform HMD. The AARRP is an augmented reality platform developed at Aalborg University and the Center for Neuroplasticity and Pain (CNAP). The platform is licensed under the GPLv3 license, which means it is open for anyone to use, also for commercial use, however all enhancements of the platform must be made available under the same license.

Any use of the platform should cite the following paper: XXX

## Showcase
![alt text](https://github.com/MThogersen/OpenAARRP/blob/master/images/AARRPv1_device_image.jpg?raw=true "Image of AARRP v1")


## Description of the AARRP
The basic build-up of the system consist of a VR HMD, in this guide the HTC Vive is used, two cameras attached to the front (from IDS imaging systems GMBH &copy;), a VR-ready computer with two (seperate) USB 3.1 ports and finally Unity 3D &copy; gaming engine and the IDS uEye SDK &copy;. Even though this guide is based on the HTC Vive, any recent VR headset supported by the Unity engine should work.


A full list of materials to build this is given here:

- VR headset (HTC Vive)
- 2 x uEye UI-3271LE cameras
	- These cameras are made for machine vision applications, they do however have great features for this applications like: 60 fps for high-resolution (2056 x 1542) recording, ready available SDK and a very small and slim form-factor.
	- You will have to contact them directly in order to get these cameras.

- 2 x USB 3.0 (or higher) 5 meter active extension cables (~Optional)
	- These cables should be used if mobility is important for the application. The specification for USB 3.0 limits it to 3 meter cables. Hence if passive (non-repeater) cables are used, they should be less than three meters and support USB 3.0. 

- 2 x USB-C male to USB A male cables with USB standard 3.0 (or higher)

- 2 x Wide-angle lenses (S-mount / M12)
	- Use lenses like [https://www.amazon.co.uk/dp/B06XWLLJRP/ref=pe_3187911_189395841_TE_dp_1](https://www.amazon.co.uk/dp/B06XWLLJRP/ref=pe_3187911_189395841_TE_dp_1 "these Xiaomi action camera replacement lenses")
	Though they are not a perfect fit for the cameras, the discrepancy is not significant and can be corrected later.

- VR-capable computer with two USB 3.0 (or higher) independent ports.
	- In a lot of computers, the USB ports are connected in a hub-like fashion inside. This means that they have reduced speed. As the cameras used for the platform requires a high bandwidth, the ports available needs to have full speed and therefore have their own PCIe-bus. If in doubt, get two USB 3.0 (or higher) PCIe-cards for the PC.

- 3D-printed mounts for the cameras and lenses (design-files are available in this Github repository)

- 8 x M1.6 (1.6mm) bolts with a 14mm length or more (optionally only two are needed if the camera protectors are omitted)

- 8 x M1.6 (1.6mm) bolts with a 30mm length or more

- 16 x M1.6 (1.6mm) regular nut (or preferably locking-nuts or with a locking washer) 

- Small strips for wire securing

- Super glue

# Build instructions

Presented below are step-by-step instructions on how to build and create a minimum working example.

## 3D-prints

In the folder "3D-prints" three files are located. Print 2 of the camera-lens holder file and one of each of the others. The camera-lens holders could be omitted, but this would require some thigtening rubber between the threading of the camera and the lens. (Note: the two HMD-mount 3D-prints are created to fit with the HTC Vive only - a new design could be created for other VR-helmets)

## Helmet assembly

**WARNING** Since the cameras are barebone electronics, there is a certain risk of damaging the electronics through Electro Static Discharge (ESD). When handling the cameras, make sure that you grab them by the lens mounting or the edges. It is a good idea to stand up (to avoid ESD-build-up between the chair and you) and wear non-synthetic clothes (wear cotton-clothing). If you need to touch other parts of the camera-board, then make sure that you are grounded (for example touch some bare-metal on a turned-off and discharged PC (i.e. once the pc is turned off, hold down the on/off button for five seconds)). In general, if you are gentle and avoid touching too much on the camera-board it should be fine. However, we take no responsability for damaged cameras. 

1. **Adding helmet mounting nuts.** Take the bottom part of the helmet mount and locate the two holes at the top of it. Drop a generous amount of super glue in the three outermost holes, insert a nut in the cutout. Do step 2. and let it dry for a couple of hours or more.
2. **Adding lens fixation nuts.** Take one of the camera protectors and locate the nut cutouts on the inner cylinder. Drop a generous amount of super glue in the three outermost holes, insert a nut in the cutout. Let it dry for a couple of hours or more. While it the glue dries, you can download and install the needed drivers and Unity3D. ( See the software setup below ).
3. **Mounting the cameras.** Grab a camera and a protector, gently press the protector ontop of the camera, so they align, note that orientation does not matter. Lay the camera/protector flat on a table, now take the lower part of the HTC Vive mount and match the four 'tubes' with the mounting holes on the board-level camera. Insert bolts in two diagonal holes, ensuring that they go through the mount, boardlevel camera and protector. While holding the assembly firm, attach nuts to both the bolts and fasten gently. Repeat this for the other two other bolts/nuts. And repeat for the other camera/protector assembly.
4. **Insert lenses.** Grab a lens and the bottom helmet mount assembly. You should feel that it sits a bit loose in the thread. To fixate it properly, add three of the small bolts that go through the nuts attached in step 2. These bolts will act as fixations for the lenses, but wait with tightening them too much, as we will have to adjust the lenses later. Repeat for the other camera.
5. **Cabling.** Run the active USB3.0 cable extenders through the loops on the back of the HTC Vive headstrap, they sit nicely with the cable end just above the top-loop. Attach USB-C male to USB-A male extensions to either camera and to the active USB extenders.
6. **Strip it.** Use strips to secure the USB-C to USB-A cables to the helmet mount (see the picture) and add some along the wires to make them run neatly together (see picture).  

## Software setup

1. Download and install the [SDK for the cameras.](https://en.ids-imaging.com/download-ueye-win64.html) Note: you will have to create a login with IDS, however, if you already bought the cameras, you will probably have a customer id anyways. The code provided here is tested to work with version XXX.
2. Check if the cameras work. Plug the cameras into your PC using the USB-C to USB-A cables. Run the uEye cockpit application and try to start one of the cameras in video-mode. Initially the output may look slow and chunky, but this is just because the settings are not optimized. (you can play around with these using the settings button).
3. Download and install [Unity3D personal edition](https://store.unity.com/download?ref=personal). The code provided here is tested to work with version XXX 
4. Download the minimum working example solution from here.
5. Test the minimum working example before lens focusing, adjustment and correction. If there is a throughput (however ugly it may be), you can continue. Otherwise there is a problem - see the troubleshooting.



#Minimum working example







