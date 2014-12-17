## Synopsis

Selinux module with additional Cobbler policy settings.

## Motivation

I run Cobbler on an Selinux-enabled host (CentOS 6.x). The default
Selinux policy is insufficient for Cobbler, causing AVC denials.

The supplied 'cobbler_local' module contains additional Selinux
policy settings for Cobbler. I have collected these over time.

## Installation

- Clone this repository
- Inspect the content of 'cobbler_local.te'
- As root, run 'seload' script to compile and install the module

## Customization

If you still suspect AVC denials with this module loaded, run the
'sefetch' script. It parses /var/log/audit/audit.log and generates
policy settings that are missing.

Merge these new additions with 'cobbler_local.te' and re-run 'seload'.

Lather, rinse, repeat.

## Tests

Load the module, run Cobbler operations as usual. You should not
see AVC denials in /var/log/audit/audit.log.

## Contributors

Ed Voncken (twitter: @EdVoncken)

## License

All content in this repository is released under MIT license, see
LICENSE.txt
