# Vehicle-Speed-Violation-Detection-System
This is a readme file for the script file for the project Speed violation detection system titled under limitspeed.
Software used - Anaconda 2021.05

sheetlink for this pre-setup: [link](https://docs.google.com/spreadsheets/d/120zxpm-IhVyBIDIkPdu8WuEHvbtunJud87ju9lOU5Lk/edit#gid=0)
(You can create your own sheet as well as drive.)

###################################################################################

For running the script. In Anaconda prompt:
1. User must create a separate environment. Certain dependencies need to be installed on the system before moving ahead with the execution.
	a. conda create --name new_env
	b. conda install pip
	c. conda install python
	d. pip install opencv-contrib-python imutils gspread oauth2client pandas pyyaml tqdm matplotlib seaborn tensorflow
	e. If GPU support is desired, ensure that CUDA CUdnn support is available in the system. If the GPU is not compatible to use CUDA, CPU will be used. Results will be satisfactory.
	 Install Pytorch using the command.
	 for CPU
	 conda install pytorch torchvision torchaudio cpuonly -c pytorch  
       for GPU with CUDA
       conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
	 Go to Pytorch.org for more information if some other configuration of system is present.
2. After installing the Pytorch dependencies replace the Upsampling file present in the address C:\ProgramData\Anaconda3\lib\site-packages\torch\nn\modules\upsampling.py by the upsampling file provided in the materials folder.
3. Run limitspeed_main.py in the source file on this new env.

####################################################################################

For using the GUI
1. There are three options in the settings 
   a. Camera :- First select which port to use in listbox.
		    i. IPcam for linking it to a portable camera. :- paste the link into the ip link box 
			 We used IP Webcam by Pavel Khlebovich availabe in the playstore.
		    ii. Camera for linking the connected camera.
		    iii. File for choosing a file from the system. Select the file from the system by navigating from the location tab.
	 Hit apply and then exit to see the changes.
   b. Parameters :- Modify the parameters on the screen
		     i. LOI 1 position is used to vary the position of the first reference line on the screen. It is changed by changing the slider.
		     ii. LOI 2 position is used to vary the position of the second reference line on the screen. It is changed by changing the slider.
		     iii. Pixel fixed distance is used to vary the pixel distance between identified vehicles to distinguish them in the system.
		     iv. Fixed distance b/w LOI is the distance contained in the two refernce lines.
			v. Speed threshold is used to set the speed limit.
	   Hit apply and then exit to see the changes.
   c. Database is used to put the google sheet token in which the information will be stored. Here the auth token is required of the gdrive.

Play and Pause buttons have been given for convenience.

####################################################################################

For getting a google sheet link to store the information in.

1. Go to google console cloud ---> "https://console.cloud.google.com"
2. Create a new project and name it as per convenience
	i. In location, keep it as it is.
3. Go to api and services -----> library.
4. Search and Download the following apis :
	i. Google drive api
  	ii. Google sheets api

----------------------------------------------

## Configuration of api ##

1. After Enabling the api, click on manage button.
2. Click on the create credentials button:-
3. In select an api select box, select Google drive api.
4. select Application Data.
5. Select "No, I'm not using them".
6. Click Next.
8. Inside Service Account Details, Select service name (Keep whatever you want).
9. If you want you can add Service Account description.
10. Click on Create and Continue.
11. In role select box, select project---> Editor.
12. Click on continue.
13. Click on Done.
14. In API/service details, 
	i. Click on Credentials tab.
	ii. In service account, click on the email.
	iii. Go to keys tab.
	iv. Select Add key drop box ---> create new Key ----> json ---> click create
	v. A JSON file will be downloaded.
	vi. Copy the downloaded json file and paste it inside the folder where you installed the app and rename it as "sheet_auth.json".

--------------------------------------


5. create a new sheet, name it "ML_project"
	i. Inside the google sheet, click on share.
	ii. Go to the downloaded json file and copy the client email.
 	iii. Give access to the client email as a editor in google sheets


--------------------------------------

###Creating a new auth token
1. Visit "https://developers.google.com/oauthplayground/"
2. Inside Select & authorize APIs, select drive api v3 ----> select "https://www.googleapis.com/auth/drive" ---> click authorize APIs button.
3. Select your gmail account ---> click on continue.
4. click on "Exchange Authorization Code for tokens" button.
5. On the right side, an access_token token will be generated.
6. Copy the access_token.
7. Paste the auth token in the Gui in the database setting.

###### APP should Work Now ########
###### We Hope our Project is useful to you :-) #####

#########################
Common Error can one see:
Keyword id error:
When the gdrive auth key is expired.
 You need to create new token and you can edit the config.json file or change the token in the GUI.

GSpread Exception: the given 'expected_headers' are not uniques:
In such case the sheet might have blank spaces in the header location which are creating common headers.
You need to clear all the sheet once again and start over the software.
