### General

1. **Start applications in background**
   
    - Telegram: `/opt/telegram/Telegram -startintray`
    
    - Google Chrome: `google-chrome-stable --no-startup-window`
    
    - Xfdashboard: `xfdashboard -d`
    
      
    
2. **Git Settings**

   - Proxy:

     ```shell
     git config --global http.proxy http[s]://userName:password@proxyaddress:port
     ```

     

3. **Uninstall all modules installed by pip**

    ```shell
    pip freeze > dump.txt
    cat dump.txt | xargs sudo pip uninstall -y
    ```
    
    On Windows rmeove all cached modules
    ```shell
    cd %USERPROFILE%\AppData\Local\pip
    del /f /s /q cache > NUL
    ```

    

4. **Softwares**

    - Libinput-Gestures

    ```shell
    sudo gpasswd -a $USER input
    sudo apt install -y libinput-tools xdotool wmctrl
    git clone https://github.com/bulletmark/libinput-gestures.git
    cd libinput-gestures
    sudo make install
    cp ./libinput-gestures.conf ~/.config/libinput-gestures.conf
    cd ..
    ```

    - R Language  

    ```shell
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
    sudo add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/'
    sudo apt update
    sudo apt install r-base
    ```
    
    - Nemo  
      Change default terminal used by nemo  
      `org.cinnamon.desktop.applications.terminal.exec` to your choice
    
      Add open terminal here shortcut
      ```shell
      mkdir -p ~/.gnome2/accels
      touch ~/.gnome2/accels/nemo
      ```
      
      Then add the following line in that file (replace "F4" with whatever shortcut you want to use):
      ```shell
      (gtk_accel_path "<Actions>/DirViewActions/OpenInTerminal" "F4")
      ```
    - Python
      ```shell
      pip install setuptools
      pip install pandas jupyter matplotlib scipy astropy ptipython
      ```
    - IDL  
      http://lifeng.lamost.org/courses/IDL/    
      Dependencies: libxp6 https://pkgs.org/download/libxp6  
      You can download and install dependencies manually from link above.  
      OR  
      Execute following commands  
      ```shell
      wget http://ftp.br.debian.org/debian/pool/main/libx/libxp/libxp6_1.0.2-2_amd64.deb
      sudo dpkg -i ./libxp6_1.0.2-2_amd64.deb
      ```
      
      Installing IDL  
      ```shell
      sudo mkdir /usr/local/itt
      sudo tar -xvf idl71_linux_x86.tar.gz --directory /usr/local/itt/
      cd /usr/local/itt
      sudo /usr/local/itt/install
      ```
      
      libraries: install coyote and astron  
      Installing idl libraries
      ```shell
      cd ~
      sudo mv /usr/local/itt/license.dat /usr/local/itt/license/
      wget https://idlastro.gsfc.nasa.gov/ftp/coyote_astron.tar.gz
      wget https://idlastro.gsfc.nasa.gov/ftp/astron.zip
      mkdir astron
      unzip ./astron.zip -d ./astron
      tar -xvf coyote_astron.tar.gz
      sudo mv ./astron /usr/local/itt/idl/lib/
      sudo mv ./pro/coyote /usr/local/itt/idl/lib/
      rm -rf ./pro
      ```
      
      
5. **Config Files**

    - ptipython: `cp ./config-files/ptipython_config.py ~/.ptpython/config.py`
    - VS Code: `settings.json`

6. **Manually add PPA**
   ```shell
   sudo apt-add-repository '<ppa technical data>'
   ```

7. **Manually add PPA Signing Key**
   ```shell
   curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0x<key>' | sudo apt-key add -
   ```
   Replacing the `<key>` with the second part of the key informed in the PPA website that you want to add.

   For example, if you find this line:
   ```shell
    4096R/7BF576066
   ```
   Use only the second part (no matter its size), which in this example is `7BF576066`

---

#### XFCE

1. **Monokai Terminal**  

    ```shell
    sudo cp ./monokai-terminal/xfce-monokai.theme /usr/share/xfce4/terminal/colorschemes
    ```
    
2. **Mac Theme**

    Prerequisites:

    ``` shell
    sudo apt install ocs-url
    ```

    window-manager theme (install Mojave-dark.tar.xz): https://www.gnome-look.org/p/1275087/

---

#### GNOME

1. **Monokai Terminal**

    ```shell
    sudo apt install -y dconf-cli uuid-runtime
    bash -c  "$(curl -sLo- https://git.io/vQgMr)"
    ```

2. **Enable hotcorners**  

    ```shell
    gsettings set org.gnome.shell enable-hot-corners true
    ```

3. **Isolate workspace windows**

    ```shell
    gsettings set org.gnome.shell.app-switcher current-workspace-only true
    gsettings set org.gnome.shell.extensions.dash-to-dock isolate-workspaces true
    ```

4. **Default Font Settings**

    ```shell
    gsettings reset org.gnome.desktop.interface font-name
    gsettings reset org.gnome.desktop.interface document-font-name
    gsettings reset org.gnome.desktop.interface monospace-font-name
    gsettings reset org.gnome.desktop.wm.preferences titlebar-font
    gsettings reset org.gnome.nautilus.desktop font
    gsettings reset org.gnome.desktop.interface text-scaling-factor
    ```
## Icons
```shell
sudo wget /usr/share/icons/google-drive -O https://seeklogo.com/images/G/google-drive-logo-C66555C645-seeklogo.com.png
```
## Clear terminal
```shell
echo "\n" >> ~/.bashrc
echo "alias cc=\"clear && printf '\e[3J'\"" >>  ~/.bashrc
```

## Gmail Filters
`{from:zomato ,from:swiggy, from:phonepe, from:paytm, slack, from:coursera, from:academia, from:decathlon, from:triaba, from:twitter, from:quora, from:notification, from:google, from:apple, from:amazon, from:mi, from:redhat,
from:redbus, from:codechef, from:teacheron, from:urbanpro, from:coinbase, from:vistara,from:github, from:ola, from:flipkart, from:prime minister,from:hackveda,from:linkedin, from:instructables, from:aliexpress, from:netgear,from:adobe}`

## Linux Mint Animation Speeds


```shell
sudo subl /usr/share/cinnamon/js/ui/expo.js
sudo subl /usr/share/cinnamon/js/ui/overview.js
```
edit the const **ANIMATION_TIME** to 0.15

you will need to restart!

## youtube-dl
Download songs playlist from youtube in mp3
```shell
youtube-dl -f bestaudio -i -x --audio-format mp3 --embed-thumbnail --add-metadata -o '%(title)s.%(ext)s' --restrict-filenames PLh4Eme5gACZE-KpXJDc4zzfBChblsFA34
```  
Download video playlist from youtube

```shell
youtube-dl -f bestvideo+bestaudio -i --add-metadata -o '%(playlist_index)s:%(title)s.%(ext)s' --restrict-filenames PL8dPuuaLjXtPAJr1ysd5yGIyiSFuh0mIL

```  
if you want to change format of video, include `--recode-video mp4` flag in above command.  

Download platlist in bestquality keeping the audio+video downloaded separately and moving converted output to a different location.
```shell
mkdir output
cd ouput
youtube-dl -f bestvideo+bestaudio -i --add-metadata -o '%(playlist_index)s:%(title)s.%(ext)s' --restrict-filenames --recode-video mp4 --exec 'mv {} ./output/{}' PL8dPuuaLjXtPAJr1ysd5yGIyiSFuh0mIL
```

## Google drive
Install grive2 https://github.com/vitalif/grive2. 

### 1. Enable Google Drive API
Go to https://console.developers.google.com/apis/library/drive.googleapis.com  
Click **ENABLE** button
<kbd>![1](https://i.imgur.com/v8xvEso.jpg)</kbd>
 
### 2. Creating secret id and code
Go to https://console.developers.google.com/apis/credentials  
Click **Create Credential** from top bar and create a **OAuth Client ID** as shown in images below:
<kbd>![1](https://i.imgur.com/eIHfpU3.png)</kbd>
<kbd>![2](https://i.imgur.com/amLrXuD.png)</kbd>

### 3. Setup
```shell
mkdir ~/google-drive
cd  ~/google-drive
```

Full Sync
```shell
grive -a --id "<secret-id>" --secret "<secret-code>"
```

Partial Sync
```shell
grive -a -s <dir-name> --id "<secret-id>" --secret "<secret-code>"
```

### Script for syncing
You can create a script like below and use it for syncing. 
```shell
#!/bin/bash

RED='\033[1;31m'
BLUE='\033[1;34m'
GREEN='\033[1;32m'
Color_Off="\033[0m"

echo -e ${RED} Starting Sync ${Color_Off}

echo -e ${BLUE}
cd ~/google-drive
grive -a
echo -e ${Color_Off}

echo -e ${GREEN} Sync Completed ${Color_Off}
read -p "Press enter to continue"

```

snapshot of script   
![1](https://i.imgur.com/vEd89NR.png)
