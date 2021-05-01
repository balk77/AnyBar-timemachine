# AnyBar-timemachine

An [AnyBar](https://github.com/tonsky/AnyBar) script to monitor the status of your Time Machine / Time Capsule backups. This script is based on the work of [@tjluoma](https://github.com/tjluoma/textbar-timemachine) but uses AnyBar instead.

-----

Here is what it looks like when a Time Machine backup is active:

<img width="85" alt="Screenshot 2021-05-01 at 20 53 55" src="https://user-images.githubusercontent.com/10166350/116792179-5c5ce780-aabf-11eb-8f47-42cc7945f4e0.png">


When Time Machine is not backing up, the dot will be hollow. On error, it will show a red exclamation mark.

I have made this script because sometimes my TimeMachine starts to [fail](https://www.google.com/search?q=time+machine+already+in+use) 

If there is another part of the Time Machine process happening, it will be shown there in a CamelCasedWord, such as:

* Copying
* DeletingOldBackups
* Finishing
* HealthCheckCopyHFSMeta
* HealthCheckFsck
* MountingBackupVol
* MountingBackupVolForHealthCheck
* Starting
* ThinningPostBackup
* ThinningPreBackup

(There may be others. Those are the only ones that I’ve noticed.)



The purpose of the script `anybar-timemachine.sh` is to parse `tmutil status` into the friendlier format shown at the top.

The files `bytes2readable.sh`, `commaformat.sh`, and `seconds2readable.sh` are all files that are used by `
ar-timemachine.sh`

## Some things to note:

- When the progress meter gets to about 90% it will stop, sometimes for a long time. Then it will say that it is finished. I’ve never seen it actually show anything above 90% completed.

- The Time Remaining can sometimes be off by a large margin, so I wouldn’t rely on it. Use it as a guide. (The “ETA” is simply a calculation of the “Time Remaining” added to the current time, so if one is wrong, the other will be too.)

- I have often seen Time Machine claiming to backup far more data than I have on my drive, sometimes far more data than could fit on my drive if it was 100% full (even when it was mostly empty). Try not to worry about that. It’s normal.

## Potential Bugs

I have _not_ tested this script with a local Time Machine drive but only with TimeMachine running off a SMB share (a network location running Ubuntu).

However, you could have multiple local drives, or multiple Time Capsule drives. If that happens, parts of this script might get confused, but the basic functionality of monitoring the process should still work fine.

## Installation

I recommend putting all four of the `.sh` files in `~/Documents/timemachine` ($HOME/$SUBDIR in the script).

Make sure they are executable: `chmod a+rx ~/Documents/timemachine/*.sh`

Once you have them installed, download and install [AnyBar](https://github.com/tonsky/AnyBar).

TODO: describe how to schedule this script

Voilà! Now you’re up and running.

## Questions?

If you have questions, create a new issue

