![](https://img.shields.io/badge/Stability-Maintained-green.svg)

# Rancher 2 Equinix Metal UI Driver

Rancher 2 UI driver for the [Equinix Metal](https://metal.equinix.com) IaaS platform.

# Note
With the upcoming EoL of Equinix Metal on June 30, 2026, this repo is being archived on February 28, 2026.


This repository is [Maintained](https://github.com/packethost/standards/blob/master/maintained-statement.md) meaning that this software is supported by Equinix Metal and its community - available to use in production environments.

## Using the Equinix Metal UI Driver

See the Rancher Documentation on [how to add a node driver](https://rancher.com/docs/rancher/v2.x/en/admin-settings/drivers/node-drivers/) to your installation. The relevant part is in 'Adding Custom Node Drivers':

1. From the Global view, choose Tools > Drivers in the navigation bar. From the Drivers page, select the Node Drivers tab. In version prior to v2.2.0, you can select Node Drivers directly in the navigation bar.
1. Click Add Node Driver Or click edit on Equinix Metal's drive if listed already.
1. Complete the Add Node Driver form. Then click Create:

    | Key               | Value |
    | ----------------- | ----- |
    | Download URL      | `https://github.com/equinix/docker-machine-driver-metal/releases/download/v0.4.0/docker-machine-driver-metal_linux-amd64.zip` |
    | Custom UI URL     | `https://equinix.github.io/ui-driver-metal/2.0.0/component.js` |
    | Whitelist Domains | `api.equinix.com` , `equinix.github.io` |

1. Wait for the driver to become "Active"
1. From the Global view, go to Clusters -> Add Cluster, your driver and custom UI should show up.

## Development

This package contains a small web-server that will serve up the custom driver UI at `http://localhost:3000/component.js`. You can run this while developing and point the Rancher settings there.

* `npm install`
* `npm start`
* The driver name can be optionally overridden: `npm start -- --name=metal`
* The compiled files are viewable at http://localhost:3000.
* **Note:** The development server does not currently automatically restart when files are changed.

## Building

For other users to see your driver, you need to build it and host the output on a server accessible from their browsers.

* `npm install`
* `npm run build`
* Copy the contents of the `dist` directory onto a webserver.
  * If your Rancher is configured to use HA or SSL, the server must also be available via HTTPS.
