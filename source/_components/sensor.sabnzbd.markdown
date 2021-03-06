---
layout: page
title: "SABnzbd"
description: "Instructions how to integrate SABnzbd within Home Assistant."
date: 2015-03-23 19:59
sidebar: true
comments: false
sharing: true
footer: true
logo: sabnzbd.png
ha_category: Downloading
ha_release: pre 0.7
ha_iot_class: "Local Polling"
---


The `sabnzbd` platform will allow you to monitor your downloads with [SABnzbd](http://sabnzbd.org) from within Home Assistant and setup automation based on the information.

To use SABnzbd with your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
sensor:
  platform: sabnzbd
  name: SAB
  api_key: YOUR_API_KEY
  host: YOUR_SABNZBD_HOST
  port: 8080
  ssl: True
  monitored_variables:
    - 'current_status'
    - 'speed'
    - 'queue_size'
    - 'queue_remaining'
    - 'disk_size'
    - 'disk_free'
```

Configuration variables:

- **host** (*Required*): The host where your SABnzbd instance is running, eg. 192.168.1.32
- **port** (*Optional*): The port to use whith SABnzbd instance. Defaults to `8080`.
- **api_key** (*Required*): Name that will be used in the frontend for the pin.
- **name** (*Optional*): The name to use when displaying this SABnzbd instance.
- **ssl** (*Optional*): Use `https` instead of `http` to connect. Defaults to False.
- **monitored_variables** array (*Required*): List of the monitored variables.
  - **current_status**: current status of the SABnzbd instance
  - **speed**: Current speed
  - **queue_size**: Size of the queue
  - **queue_remaining**: Remaining elements in the queue
  - **disk_size**: Disk size of the storage location
  - **disk_free**: Free disk space at the sotrage location

Note that this will create sensors under the name 'sab' and NOT 'sabnzbd' as follows:

```
 - sensor.sab_status
 - sensor.sab_speed
 - sensor.sab_queue
 - sensor.sab_left
 - sensor.sab_disk
 - sensor.sab_disk_free
```

As always, you can determine the names of sensors by looking at the dev-state page `< >` in the web interface.
