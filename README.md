# Changing the Vodafone Power Station SSID

This repository is meant to provide a step-by-step guide to change the SSID of the Vodafone Power Station.

Your router stores the settings for your home Wi-Fi network. If you want to change something on your network, you have to log in to your router. From there, you can change the SSID, modify the password, adjust the security level, and set up or alter a variety of other options. However, on the Vodafone Power Station, you are not allowed to (completely) rename your network unless you follow this step-by-step guide.
But before you can do all that, you first need to gain access to your router.

## Log in to your router using a web browser

You can connect to your router wirelessly or using an Ethernet cable. To access your router's login page, open a web browser and enter your router's login URL or default IP address.
You can usually find your router's login URL or default IP address on the back or bottom of your router. These parameters should be as follows:

| URL           | [http://vodafone.station/login.html](http://vodafone.station/login.html) |
|------------   |:------------------------------------------------------------------------:|
| IP address    | 192.168.1.1                                                              |

Since that's not always the case, you may first want to confirm the address of your router.

### Find your router's IP address on Windows

To find your router's IP address, type `cmd` in the Windows search bar and open _Command Prompt_. Once the command prompt is opened, type `ipconfig` and press _Enter_ to run the command. Scroll through the information until you see a setting for Default Gateway under Ethernet adapter or Wireless LAN adapter. That's your router, and the number next to it is your router's IP address.

### Enter your router login username and password

After you type the IP address, you're asked for a username and password to access your router. These login credentials are different from the ones you use to connect to your Wi-Fi. This is either the default username and password for your router, or the default username and a unique password that you may have created when you set up the router. If you don't remember your login credentials, signing in becomes a bit trickier.

## Rename the network

After you gain access to your router, select the WiFi tab from the web interface and open the developer tools then, right-click the _apply_ button and select _inspect_. At this point select the _Event Listeners_ tab, expand _click_ and you should see _applyButton_ as the second listener to its right should be visible `debugger:VMnnnn`. Click on it and you will see some JavaScript code. Scroll down and look for the following string[^1]: `wifi_ssid_guest = 'Vodafone'+$('.ssid-input3').val()`

The above line of code is followed by a grayed out code after which you will find the following line of code: `data_format.push(...)`. Here you have to add a breakpoint clicking the line number on the left.
Then, make some changes in order to enable the _apply_ button (e.g., edit the network name) and click on it.
Code execution will stop at the breakpoint thus, you can open the _Console_ tab and launch the following command:

```
wifi_ssid='SSID';
wifi_ssid_5g='SSID_5G';
wifi_ssid_guest='SSIDGUEST';
```

replacing text between quotes with the desired ones. Once the command is executed you should see a confirm with the new value. It is now possible to resume the script execution using the right panel.

[^1]: You can use ctrl+F to quickly find the string.

### Note

You will need to perform this procedure every time a change is made.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
