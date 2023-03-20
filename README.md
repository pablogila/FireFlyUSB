# FireFlyUSB

Need to use a public computer often? Tired of adding and removing your accounts every day? No problem! FireFlyUSB is a set of scripts that make it extremely easy to take your Firefox profile with you on an USB, to use it on public computers without worrying about exposing your data.   


## Usage

Every time you want to use your Firefox Profile, connect your USB, go to your folder in the public computer, execute `COPY.sh`, and open Firefox with `FIREFOX.sh`. When you are done, execute `CLEAN.sh` to remove your data from the computer.  

Sounds easy right? Let's see how to configure it.


## Download

On GitHub, click on **Code** and then **Download ZIP**.  
Or if you prefer using **Git**, run: `git clone https://github.com/pablogila/FireFlyUSB.git`  


## Prepare your Firefox Profile

The first thing is to create your Firefox Profile, with all the accounts, extensions and configurations that you want to carry around. In order to do this, go to the public computer, open a terminal and write:  

`firefox -P`  

A window will open, asking you to select a profile. Take a look on the default profile to restore it later; it is usually called **default-release**. Click on **Create profile**, click **Next**, and then type a name for your profile, such as `MyFirefoxProfile`. Click on **Choose folder**, and create a folder where you usually work, e.g.,  

`/home/USER/FOLDER/MyFirefoxProfile/`  

You will have to copy later the `CLEAN.sh`, `COPY.sh` and `FIREFOX.sh` scripts to the parent folder, in this case, `/home/USER/FOLDER/`. Note that if you choose a name other than **MyFirefoxProfile**, you will need to update it within all the scripts.  

Now start customizing your Firefox. Remember to check the **Delete cookies and site data when closing Firefox** option in the **Privacy and Security** panel. You can add exceptions to this deletion if you wish. When you are done, close Firefox, compress your `MyFirefoxProfile` into a `MyFirefoxProfile.zip`, and copy this zip to your USB.  


## Get the scripts ready

If you didn't do it before, copy the `CLEAN.sh`, `COPY.sh` and `FIREFOX.sh` scripts to the parent folder of your Firefox Profile, in this case, `/home/USER/FOLDER/`.  

You will now modify the `COPY.sh` script. You need to write both paths of your zip file, so that when you execute the script, the zip from your USB will copy and extract to the public computer:  

`cp /USB_PATH/MyFirefoxProfile.zip /PUBLIC_PC_PATH/MyFirefoxProfile.zip`  

The `COPY.sh` script should look somewhat like this:  

```shell
#!/bin/bash

cp /media/home/USB/FireFly/MyFirefoxProfile.zip /home/USER/FOLDER/MyFirefoxProfile.zip

unzip MyFirefoxProfile.zip
```

Then make all bash scripts executable, with the following command:  

`chmod u+x CLEAN.sh COPY.sh FIREFOX.sh`  

Finally, return Firefox to normal for the rest of the users by running `firefox -P`, select **default-release**, click **Use the selected profile at start-up without asking** and **Start Firefox**. Confirm that this is the public profile for the browser, and exit.  

You can now check that both your profile zip and folder are removed when you execute `CLEAN.sh`. Congratulations! you have succesfully configured all the FireFlyUSB scripts.  


## Final Considerations

If you ever want to change your Firefox configuration or add new extensions or accounts, you will have to compress your folder into a zip again and overwrite the one from your USB.  

Note that **COPY.sh** does not send your files to the trash. If you find any of your zip files or folders in the trash, **delete them permanently**.  

You are always exposed on a public computer. FireFlyUSB scripts can help remove most of your traces, but know that this does not protect you from an attack over the network. Also, even deleted files can be recovered with a file recovery program like Recuva, so be careful what you do.  

I am in no way an expert in computer security, so **use these scripts at your own risk**. If you find a flagrant security hole, please let me know.  

In principle you could create your Firefox profile folder directly inside the USB, but at least in my experience it runs sloooooow. This is the reason for FireFlyUSB.  

These scripts are written for Linux under the GPL-3.0 License. Feel free to share, edit and adapt them; it would not be hard to translate them for Windows if you want.  

Last but not least, **thank you for using FireFlyUSB**. Have a nice day :D  
