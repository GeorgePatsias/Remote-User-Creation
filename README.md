# Remote Server User creation

A script which allows the creation of a User remotely to a Linux Server.

## Definition
Must have SSH root access to the server to execute this.
* SSH to the server.
* Uses ```adduser``` to create a new User profile.
  * ```--gecos ''``` Bypass General information for the user.
  * ```--disabled-password``` Do not run ```passwd``` to set the password.
* Prints in the shell the username:password pair and pipe it to ```chpasswd``` which updates the user that we created before.
* Change the date of the last password change date to 0.
* Create a .ssh directory in the User's profile.
* Injects the SSH key to the ```authorized_keys``` file.
* Adds the User to the ```Sudo``` group.

## Usage
#### Parameters <Domain Name> <User Name> <Default Password> <SSH Key Path or Text>
```bash
chmod +x add_user.sh
./add_user.sh example.com john Password123 "ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA879BJGYlPTLIuc9/R5MYiN4yc/YiCLcdBpSdzgK9Dt0Bkfe3rSz5cPm4wmehdE7GkVFXrBJ2YHqPLuM1yx1AUxIebpwlIl9f/aUHOts9eVnVh4NztPy0iSU/Sv0b2ODQQvcy2vYcujlorscl8JjAgfWsO3W4iGEe6QwBpVomcME8IU35v5VbylM9ORQa6wvZMVrPECBvwItTY8cPWH3MGZiK/74eHbSLKA4PY3gM4GHI450Nie16yggEg2aTQfWA1rry9JYWEoHS9pJ1dnLqZU3k/8OWgqJrilwSoC5rGjgp93iu0H8T6+mEHGRQe84Nk1y5lESSWIbn6P636Bl3uQ== your@email.com"
```