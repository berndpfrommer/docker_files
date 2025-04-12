# Docker container for FLIR Spinnaker

This is a hacked version of the [XRDP Server for GUI in Docker
Container](https://github.com/satishweb/docker-xrdp)

What's missing is a hacked version of the Spinnaker SDK:
```
spinnaker-4.2.0.46-amd64-22.04-pkg.tar.gz
```
where the following section has been removed from configure_spinnaker.sh:
```
26,63d25
< echo "Adding new members to usergroup $grpname..." 
< while :
< do
<     # Show current members of the user group
<     users=$(grep -E '^'$grpname':' /etc/group |sed -e 's/^.*://' |sed -e 's/, */, /g')
<     if [ -z "$users" ]
<     then 
<         echo "Usergroup $grpname is empty"
<     else
<         echo "Current members of $grpname group: $users"
<     fi
< 
<     echo "To add a new member please enter username (or hit Enter to continue):"
<     echo -n "$MY_PROMPT"
<     read usrname
<     if [ "$usrname" = "" ]
<     then
<         break
<     else
<         # Check if user name exists
<         if (getent passwd $usrname > /dev/null)
<         then
<             # Get confirmation that the username is ok 
<             echo "Adding user $usrname to group $grpname group. Is this OK?"
<             echo -n "$MY_YESNO_PROMPT"
<             read confirm
<             if [ "$confirm" = "y" ] || [ "$confirm" = "Y" ] || [ "$confirm" = "yes" ] || [ "$confirm" = "Yes" ] || [ "$confirm" = "" ]
<             then
<                 # Create user group (if not exists) and add user to it
<                 groupadd -f $grpname
<                 usermod -a -G $grpname $usrname
<                 echo "Added user $usrname"
<             fi
<         else
<             echo "User "\""$usrname"\"" does not exist"
<         fi
<     fi
< done
```
