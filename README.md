# Charge Limit - Linux
#### A systemd service to set battery charge limits on Linux

## Usage
To install, copy `chargelimit.service` to `/etc/systemd/system/chargelimit.service`.

* To limit battery level to 60%, `sudo systemctl start chargelimit`
* To remove the charge limit, `sudo systemctl stop chargelimit`
* Enable limiting startup, `sudo systemctl enable chargelimit`


This is one of those on-off repositories that should actually be a gist.
If you have any questions or ideas for improvement, feel free to create an issue or a pull request :)
