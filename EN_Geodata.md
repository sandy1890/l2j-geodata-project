In this tutorial I will teach you how to make your own Geodata!

Tools needed.

Stazis L2 Geo Converter (GeoConv)
Download: GeoConv\_v93b.zip

G16ed (A heightmap editor that works directly with the UEd3 G16 format (16-bit greyscale.))
Download: G16ed.zip

UTPackage (extract)
Download: UTPackage.zip

Unreal Engine 2 Editor (Create UTX)
Download: UE2Runtime-22261903.zip

L2J-GeoEditor (Convert to L2J format and create the PathNode)
Download: l2j-GeoEditor-v17.zip

HEX Editor - (I use UEStudio or Ultraedit)
Download: Find it on the web :P

Important: In this example I will use the map T\_22\_19, but applies the same procedure for any map.

First we need to extract heightmap images from UTX files (T\_22\_19.UTX, T\_22\_20.UTX etc.)

**Put this file T\_22\_19.UTX in UTPackage/Textures and execute "unpack.bat"** Open UTPackage/RAW folder and find the file 22\_19.raw
**Open this file with Ultraedit and search (Ctrl + f) for "40 80 10", the first byte after this string is the start of the heightmap image.** Copy this address, in this case is 107h
**Open the windows calculator and switch to "Scientific" mode, select "Hex" and input "107", select "Dec" and now you have "263".** Open G16ed, go to "File -> Import -> RAW data, search for 22\_19.raw and in the field "Data start offset" input "263" and click in Input, Ok, Ok.
**Go to "File -> Save (Ctrl + S)" and use the name of the map for your new image (22\_19.BMP). Now you have a perfect G16 heightmap image.**


Now we need to create an UTX file with the image that we have saved.

**Open UnrealEd and in the windows "Textures" go to "File -> New" and complete the fields.**

Info -> Package: T\_22\_19, Group: Height, Name: 22\_19, Class: Raw Material
Properties -> MaterialClass: Class"Engine.Texture" (Select Texture from drop-down)

**Go to "File -> Import" and select the image 22\_19.BMP and ensure that the fields are correct.**

Info -> Package: T\_22\_19, Group: Height, Name: 22\_19
Options -> Masked: uncheck, Generate MipMaps: uncheck, Detail Hack?: uncheck, Compression: none

**Go to "File -> Save" and save this file as T\_22\_19.utx.**

Now we can create our Geodata using Stazis L2 Geo Converter (GeoConv)

**Navigate to the Textures folder in the game, rename your original T\_22\_19.utx to T\_22\_19\_O.utx and put in this folder our new T\_22\_19.utx** Open GeoConv and change this params.

Min Plane Angle to XY: 20, Stairs Height: 10, Optimization Different: 80

**Click "Open Packages" and select 22\_19.unr in "Lineage II/MAPS", allow the process to finish and now you have your GEO 22\_19\_conv.dat in the folder "Lineage II/MAPS".** Convert this GEO to L2J format and create the PathNode with L2j GeoEditor or HDGE.


Known Issues

**Some geodata are not correctly generated or can't be generated.** Using "Stairs Height: 10" can cause problems with the stairs (If you use "8" check all the stairs in the map for correct NSEW).
**...**


PD: Guide taken from http://www.plopixel.com/tienda-en-linea/7-lineage-2/7-make-your-own-lineage-ii-freya-geodata