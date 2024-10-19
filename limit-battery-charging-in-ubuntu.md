To limit the battery charge on Ubuntu 24.04, you can use TLP or vendor-specific tools, depending on the manufacturer of your laptop (e.g., Lenovo, Dell). Limiting the charge helps prolong the battery life by keeping it from constantly charging to 100%.

Here’s how to set it up:

Using TLP (General Solution for Most Laptops)
TLP is a power management tool for Linux that works with a variety of laptops and allows you to limit battery charging.

Install TLP
You can install TLP with the following commands:
```
sudo apt update
sudo apt install tlp tlp-rdw
```
Configure Charge Limits
After installation, you'll need to edit the TLP configuration file to limit the charging threshold.
Open the configuration file:
```
sudo nano /etc/tlp.conf
```
Look for these lines and uncomment them (remove the # at the beginning), then set the values to your desired charging thresholds:
```
# Battery charge thresholds for ThinkPads only
# Charging starts when the charge level is below:
START_CHARGE_THRESH_BAT0=40
STOP_CHARGE_THRESH_BAT0=80v
```
* START_CHARGE_THRESH_BAT0: This sets the threshold at which charging will start (e.g., 40%).
* STOP_CHARGE_THRESH_BAT0: This sets the threshold at which charging will stop (e.g., 80%).
Adjust the values according to your preference.

Save and close the file (Ctrl + O, then Enter, followed by Ctrl + X to exit).

Restart TLP to apply the changes:
```
sudo systemctl restart tlp
```
