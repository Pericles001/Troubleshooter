## add a new user

- useradd (-m: gives a home directory folder to user -s: set the default shell /usr/bin/zsh) __uname__

- passwd uname (Define a password to user)

- adduser uname sudo (Add user to sudoers list)

- userdel (-r: removes all configuration files for the user) uname

- cat /etc/passwd | awk -F: '{print $1}' (read all the users in linux)

## list all users 

- cat /etc/passwd | awk -F: '{print $1}'\n

## delete a user

- userdel -m username
