# Remove '=' from the list of filename in Vim
:set isfname-==

# Interpret SELinux auth messages
ausearch --interpret --exit -13

# Man for bash (or long pages)
* help read
* help -m read (man-page-like formatting)
* /^\s*case

# Write file even if opened without sudo
:w !sudo tee % 

# Searching for section, then replacing in the section
sed -i '/<interface name="public">/,/<\/interface>/ s/<inet-address value=".*"\/>/<inet-address value="'$ntfTrafficIp'"\/>/g;'
sed -i '/what_to_find/s/change_this/to_that/'

# Firefox scroll issue (GTK3)
DK_CORE_DEVICE_EVENTS=1 firefox
