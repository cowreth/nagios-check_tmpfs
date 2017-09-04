# NRPE Plugin : check_inodes 

This simple Nagios NRPE plugin will check all tmpfs filesystems to check free space.

It's based on the output from "df", parsed with awk to get the percentage of used inodes. 

It then echo the results as requested per NRPE.

## Usage

Put the script in your NRPE scripts directory.

Update your nrpe.conf with this line : 

`
command[check_tmpfs]=/usr/bin/sudo /opt/scriptsnagios/check_tmpfs -w 80-90 -c 91-100
`

The script checks each filesystem for usage. It's based on the 'df' command output and may run on any system having it (though it comes as is regarding any warranty).

`check_tmpfs [-w warningThreshold] [-c criticalThreshold]`
 
_Note :_ -w and -c have default values.

__Options__

* -w RANGE : set the warning threshold. E.g. : 80-90 to match usage between 80% and 90% included
  * Default : 80-90
* -c RANGE : set the critical threshold. E.g. : 90-100 to match usage between 90% and 100% included
  * Default : 90-100
* -h
  * Get some help
