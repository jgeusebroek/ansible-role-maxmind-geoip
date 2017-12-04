[![Build Status](https://travis-ci.org/jgeusebroek/ansible-role-maxmind-geoip.svg?branch=master)](https://travis-ci.org/jgeusebroek/ansible-role-maxmind-geoip)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-maxmind--geoip-blue.svg)](https://galaxy.ansible.com/jgeusebroek/maxmind-geoip)

# Ansible role: maxmind-geoip

An Ansible Role that installs and configures the Maxmind GeoIP databases.

## Requirements

None

## Dependencies

None

## Example Playbook

    ---
    - hosts: all
      sudo: yes

      roles:
         - { role: jgeusebroek.maxmind-geoip, tags: ["maxmind-geoip"] }

## Example Variables

Below are configurable variables with there default values.

	# Debian
	maxmind_update_package_jessie:
		'http://ftp.nl.debian.org/debian/pool/contrib/g/geoipupdate/geoipupdate_2.2.2-1_amd64.deb'

	NOTE: Debian Jessie does not have a package for geoipupdate, that's why we install a version from 'sid'. This a workaround.

	# Credentials (these defaults are for the free databases)
	maxmind_update_userid: '999999'
	maxmind_update_licensekey: '000000000000'

	# These are the free databases, should you have a subscription change these values
	maxmind_update_product_ids:
	# - GeoLite2-City
	# - GeoLite2-Country
	  - GeoLite-Legacy-IPv6-City
	  - GeoLite-Legacy-IPv6-Country
	  - 506
	  - 517
	  - 533

	NOTE: Debian Jessie only supports the legacy databases, which is why I have those as default.

	# Every tuesday the databases get updated at Maxmind
	# The free databases are only updated the first tuesday of the month
	maxmind_cron_weekday: 2
	maxmind_cron_hour: 6
	maxmind_cron_minute: 13

	# Optional e-mail address to send cron results
	maxmind_cron_email: ""

## Other Information

The Maxmind GeoIP databases is downloaded to the `/usr/share/GeoIP/` directory on Ubuntu operating systems.

## License

MIT / BSD

## Author Information

2015 - 2017 by [Jeroen Geusebroek](http://jeroengeusebroek.nl/).
