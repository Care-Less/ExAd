# ExAd v1.0.4
 Upload of ExAd Created by an unknown previous coder

Disclaimer, This is not made by me, this is purely a reupload as the exile forums are no longer with us.

Instalation Instructions:


Step 1: Copy the files located in the "@ExileServer\addons" folder into your servers "@ExileServer\addons" 
Note: Do not copy over "exad_vg" if you do not wish to utilize the ExAd Virtual Garage.

Step 2: Open the "@ExileServer\extDB\sql_custom_v2" folder and follow steps within "exile.ini"
Note: If you are not using ExAd VG disregard those steps. Also if using extDB3 utilize steps within (64-bit) folder.

Step 3: Copy the folder "ExAdClient" located within mission folder into your own mission (i.e. Exile.Altis)

Step 4: Open the file "config.cpp" and follow steps.
Note: If you did not include ExAd VG in previous steps ensure to remove it here as well.

Step 5: Open the "CfgExileCustomCode.cpp" and follow steps.
Note: Same thing applies here if you are not using ExAd VG.

Step 6: Open the "CfgInteractionMenus.cpp" and follow steps.
Note: If not using Recruit AI app don't include the bodyguard block.

Step 7: Open the "description.ext" and follow steps.

Step 8: Copy the file "stringtable.xml" into your mission pbo.

Step 9: Apply the necessary additions to your BattlEye "scripts.txt" and "remoteexec.txt".

Step 10: If using ExAd Virtual Garage apply the following Query to your MYSQL database:

ALTER TABLE `vehicle` ADD `territory_id` INT(11) UNSIGNED NULL DEFAULT NULL;
ALTER TABLE `vehicle` ADD CONSTRAINT `vehicle_ibfk_2` FOREIGN KEY (`territory_id`) REFERENCES `territory`(`id`) ON DELETE CASCADE ON UPDATE RESTRICT;

Note: If you have done this previously you can skip this step.

I have included original ExAd documentation if you get confused with any of these steps.

IF YOU DON'T WANT EXAD VIRTUAL GARAGE REMOVE THE FOLLOWING LINES:

Under "class XM8" remove:

class ExAd_VG
    {
        title = "Virtual Garage";
        controlID = 50000;                  //IDC:50000 -> 50015 || These need to be unique and out of range from each other
        logo = "ExadClient\XM8\Apps\VG\Icon_VG.paa";
        onLoad = "ExAdClient\XM8\Apps\VG\onLoad.sqf";
        onOpen = "ExAdClient\XM8\Apps\VG\onOpen.sqf";
        onClose = "ExAdClient\XM8\Apps\VG\onClose.sqf";
    };
	
Also remove "ExAd_VG" from Extra apps.

For the app buttons find:

class XM8_App13_Button: RscExileXM8AppButton1x1
{
    textureNoShortcut = "ExadClient\XM8\Apps\VG\Icon_VG.paa";
    text = "ExAD Virtual Garage";
    onButtonClick = "['ExAd_VG', 0] call ExileClient_gui_xm8_slide";
    resource = "";
};

and replace with:

class XM8_App13_Button: RscExileXM8AppButton1x1
{
    textureNoShortcut = "";
    text = "";
    onButtonClick = "";
    resource = "";
};