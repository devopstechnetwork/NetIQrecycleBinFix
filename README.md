NetIQrecycleBinFix
==================

A script that looks for orphaned group objects in the NetIQ Directory &amp; Resource Administrator's Recycle Bin and correlates them to active user objects in Active Directory

USAGE -- NetIQrecycleBinFix [OPTIONAL: Path]

REQUIREMENTS: Powershell 2.0 or above (including in Windows 7 and Windows 8/8.1). Active Directory Users and Computers, or Remote Server Administration Tools

RSAT for Windows 8.1: http://www.microsoft.com/en-us/download/details.aspx?id=39296

RSAT for Windows 8: http://www.microsoft.com/en-us/download/details.aspx?id=28972

RSAT for Windows 7: http://www.microsoft.com/en-us/download/details.aspx?id=7887

This script looks for orphaned objects in the NetIQ Directory & Resource Administrator tool's recycle bin and correlates them to enabled AD user objects in an effort to determine if any object had been removed from the Recycle Bin using any tools other the NetIQ DRA. The script outputs a CSV with all the relevant objects that can be deleted by an administrator. 

Background: When NetIQ Directory & Resource Administrator (DRA) sends an object to the Recycle Bin, it creates a hidden group object that contains all of the group memberships the now-recycled object once contained.

If the deleted object is restored via native active directory administrative tools, this group oject becomes orphaned; and more alarmingly, DRA cannot delete an object with an orphaned group object in the recycle bin.