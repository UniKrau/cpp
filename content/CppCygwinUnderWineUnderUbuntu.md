[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's tools](Tools.htm).

 

 

 

 

 

([Tool](Tools.htm)) [Running Cygwin under Wine under Ubuntu](CppCygwinUnderWineUnderUbuntu.htm)
===============================================================================================

 

  ---------------------------------------------------------------
  ` Cygwin does not appear to run well under Wine under Ubuntu`
  ---------------------------------------------------------------

 

To run [Cygwin](CppCygwin.htm) under [Wine](CppWine.htm), follow \[1\]:

-   Navigate to \~/.wine/drive\_c/cygwin
-   wineconsole cmd
-   Cygwin.bat

 

For me, this resulted in

-   [the Cygwin shell (png)](CppCygwinUnderWineUnderUbuntu.png)
-   [the wineconsole shell (png)](CppCygwinUnderWineUnderUbuntu2.png)

 

Note the error (in the Cygwin shell):

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` CMD Version 1.2  C:\cygwin>Cygwin bash: /dev/null: No such file or directory bash: cannot create temp file for here document: Invalid request code Your group is currently "passwd/group_GID_clash(gid/pgsid)".  This indicates that your gid is not in /etc/group, but the pgsid (primary group associated with your SID) is in /etc/group.  The /etc/passwd (and possibly /etc/group) files should be rebuilt. See the man pages for mkpasswd and mkgroup then, for example, run  mkpasswd -l [-d] > /etc/passwd mkgroup  -l [-d] > /etc/group  Note that the -d switch is necessary for domain users.`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Creating a folder /home/richel/.wine/drive\_c/cygwin/dev/null fails.

 

Also note the many errors (in the wineconsole shell):

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` [many more] fixme:ntdll:NtQueryVolumeInformationFile 0x1c: volume info not supported fixme:ntdll:NtQueryVolumeInformationFile 0x1c: attribute info not supported [many more]`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

External links
--------------

 

-   [Wine bugtracker](http://bugs.winehq.org/show_bug.cgi?id=443)
-   [Wine page about running Cygwin under
    Wine](http://wiki.winehq.org/CygwinSupport)

 

 

 

 

 

[Go back to Richel Bilderbeek's tools](Tools.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)