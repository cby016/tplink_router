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
