# Changelog

This change log contains the history of changes to the Portainer Templates.

## 1.3.7

* Generic changes:
  * Migrated the old docker-compose repository to the _raw folder, which now holds the raw compose files.
  * Updated all Portainer Templates labels and relative descriptions in standard 1940-00017.
  * Updated all compose files to match the newly defined tree structure in standard 1940-00017.
  * Add "hostname" where missing or fix where incorrect (not appending the $INSTANCE_NAME) to conform to standard 1940-00017.
  * Remove version from all compose files, as it has been obsoleted.
  * Update external networks declaration to reflect the latest Docker directives.
  * Remove IFACE_AOIP and IFACE_EXT from macvlan (single/dual) template files as a default value is provided in the compose file and should not be changed.

* Forza changes:
  * Renamed all remaining instances of "Forza" to "Forza HDS" or "Forza FM" accordingly. This fixes a potential conflict where FM and HDS version with the same $INSTANCE_NAME write to the same data folder.
  * Added Forza FM components (Forza & FM Transport) with host networking to edge-templates-v3.
  * Remove IFACE_WEBUI from Forza HDS host compose file as it is deprecated and not needed.

* Coturn changes:
  * Added standalone Coturn macvlan compose file and template. Previously only available via the WebRTC Service or standalone with host networking.

* Zephyr Connect:
  * Updated the following environment variables to match standard 1940-00017 in single macvlan compose file: IFACE -> IFACE_AOIP

## 1.3.6

* EoL GitLab Portainer Templates as we moved to GitHub for public-facing files.
* Update GitLab Portainer Templates Development to match GitHub Portainer Templates.
  * Updated compose files for Forza, Forza FM Service and FM Transport from various versions.
  * Imported templates-v3 from GitHub.
  * Imported PDMx 1.3.5 changes.
* General cleanup
  * Rename ZConnect single-macvlan to macvlan to fit naming scheme.
  * Change internal-templates-v2 ordering to match v3 to ease comparaison.
  * Change templates-v2 ordering to match v3 to ease comparaison.

## 1.3.5

* Update PDMX templates with dual-macvlan
* Update Host PDMX templates to be able to specify a specific NIC for AoIP

## 1.3.4

* Release Portainer templates V3

## 1.3.3

* Correct Forza HDS Dual Macvlan

## 1.3.2

* Release PDMX

## 1.3.1

* Release Forza FM
* Update label for Forza to Forza HDS

## 1.3.0

* Release WebRTC service
* Place Telos Alliance products first in template list.

## 1.1.4

* Correct Forza Dual Macvlan template-v2.json

## 1.1.3

* Correct Forza volume
* Add second macvlan to Forza dual macvlan template

## 1.1.2

* Add volume to make Altus Logs persistent

## 1.1.1

* Correct missing non-root templates

## 1.1.0

* Add non-root support for VXS
* Add PTP-Snooping support or VXS
* Add non-root support for Forza
* Update environment variables for Forza
* Add PDMX to internal-templates-v2.json
* Correct NDI issue in Altus
* Add Infinity Link to internal-templates-v2.json
* Correct Zephyr Connect to be functional
* Correct Coturn template
* Remove Coturn and Beacon from templates-v2.json
* Add Vero to internal templates
* Add Dual macvlan support for the following products
  * Altus
  * VXS
  * Zephyr Connect
  * Forza
* Update README.md to further explain templates and compose files further
* Create this change log
* Create vip-templates.json

## 1.0.0

* initial release of portainer templates
