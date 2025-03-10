# MikroTik Tor Blocklist

This project allows you to download the latest Tor IP blocklist and import it into your MikroTik router.

## Features

- Download the latest Tor IP blocklist
- Remove existing Tor IP entries
- Import the new Tor IP blocklist into MikroTik

## Usage

/tool fetch url="https://github.com/tntclouds/mikrotik-blocklist/raw/main/tor_exit_blocklist.rsc" mode=https
/ip firewall address-list remove [find where list="tor_exit_blocklist"];
/import file-name=tor_exit_blocklist.rsc


## Scheduler (Optional)
To keep the blocklist updated automatically, set up a scheduler:
/system scheduler
add name="Update Tor Blocklist" interval=1h on-event="/tool fetch url=\"https://github.com/tntclouds/mikrotik-blocklist/raw/main/tor_exit_blocklist.rsc\" mode=https; /ip firewall address-list remove [find where list=\"tor_exit_blocklist\"]; /import file-name=tor_exit_blocklist.rsc"
