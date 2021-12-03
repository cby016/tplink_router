# TPLink Router Device Tracker for Home Assistant

Recently the tplink device tracker code was [removed](https://github.com/home-assistant/home-assistant/pull/27936) from Home Assistant. 

This repository allows users to create a custom component and continue to use the tplink device tracker.

Installation:
1. In the Home Assistant config folder, create a custom_components/tplink_router folder.
2. Copy \_\_init__.py, device_tracker.py and manifest.json from this repository into the new folder.
3. Restart Home Assistant
4. Add the device_tracker / tplink_router configuration into the configuration.yaml file.
5. Restart Home Assistant


Example Config:

```
device_tracker:
  - platform: tplink_router
    host: ROUTER_IP_ADDRESS
    username: ROUTER_USERNAME
    password: !secret tplink_router_password
```

To verify Home Assistant is seeing the devices that are connected to the router, navigate to Developer Tools -> States and search for entities that start with device_tracker. The devices should show up with a source_type attribute of router.

A known_devices.yaml file should be created that can be edited to further customize the appearance of the tracked devices. For more information see https://www.home-assistant.io/integrations/device_tracker/.



For XDR Series, the password encryption algorithm is still unknown, so a encrypted password has to be used:
 1. Go to the login page of your router. (default: 192.168.0.1)
 2. Type in the password you use to login into the password field.
 3. Open the Network monitor of your browser (usually by pressing F12 and then clicking on "Network").
 4. Clear the screen before pressing "Confirm"
 5. Upon successful login, right click on the first one and select "Copy as cURL"
 6. Paste the content somewhere else and copy the value of the password in the last line without the quotation marks
    (example: --data-binary '{"method":"do","login":{"password":"**SoMeEnCrYpTeDtExT**"}}')
