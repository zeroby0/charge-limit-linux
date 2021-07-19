# Charge Limit

Stops charging you laptop when it reaches 60% charge. 

To install, run:
 ```bash
 curl "https://git.io/JWbU9" | sudo tee /etc/systemd/system/chargelimit.service
 

 sudo systemctl start chargelimit # set limit till next system restart
 sudo systemctl enable chargelimit # set limit automatically every time system restarts 
 ```
 
## FAQs
### Why should I limit my charge?

Keeping your battery's charge between 40% and 60% will improve it's lifespan and capacity.

**Note**: You should disable the limit, and let your battery charge to 100% and then completely discharge once every 3-4 months.

### How do I change the limit?

Open the `/etc/systemd/system/chargelimit.service` file in a text-editor of your choice, go to line 7, and replace `60` with your preferred value.
Use `sudo` to open if it says permission denied.

### How do I remove the limit?

To remove the limit, run:
```bash
sudo systemctl stop chargelimit # removes limit till next system restart
sudo systemctl disable chargelimit # removes limit till you manually turn it back on
```

You may also remove the systemd service file if you want to completely uninstall the program:
```
sudo rm  /etc/systemd/system/chargelimit.service
```

### How does it work?

You can write your preferred charge limit to this file: `/sys/class/power_supply/BAT0/charge_control_end_threshold`, and the kernel stops charging the battery when it's at the limit.

But the value you write is reset to `100` when your laptop restarts. This program uses `systemd-services` to write the limit to the file every time your computer restarts.


[Read more about systemd services](https://www.linode.com/docs/guides/introduction-to-systemctl/)


## License

Everything in this repository is released into public domain and is using [Unlicense](https://github.com/zeroby0/charge-limit-linux/blob/main/LICENSE).

This is one of those one-off repositories that should probably be a gist.
If you have any questions or ideas for improvement, feel free to create an issue or a pull request :)
