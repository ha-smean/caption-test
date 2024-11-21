# link github account to terminal

### Generate the SSH key

Type the following, replacing <your email address> with the email address that is linked to your Github account, and hit Enter:  
```ssh-keygen -t rsa -b 4096 -C "your email"```  
*generates a new SSH key*  

Next, you will be prompted to enter a directory to save the key, press ```Enter``` to accept the default location.  
You will then be prompted to choose a passphrase. I prefer not to have a passphrase; so just press Enter and Enter again to confirm the empty passphrase.  


Navigate to into the *.ssh subdirectory*   
```cd ~/.ssh```  

Finally, you will need to add the SSH key to the ssh-agent, which is meant to help with the authentication process. To do that, first you need to start the ssh-agent, so run the following in Terminal:  
```eval "$(ssh-agent -s)"```  


### Create config file 
Check if your .ssh directory contains a file named config. If it does, modify it so that its content is the following:  
```
Host *
 AddKeysToAgent yes
 UseKeychain yes
 IdentityFile ~/.ssh/id_rsa
 ```
If your .ssh subdirectory does not contain a file named config, then create one:  
and paste the above as its content  

```
touch config
nano config
```  

Finally, add the key to the agent by running the following in Terminal:  
```ssh-add -K ~/.ssh/id_rsa```

### Add the Key to your Github Account
Copy the public version of your key to the clipboard buffer, with the following command:  
```pbcopy < ~/.ssh/id_rsa.pub```  

Go to your Github account profile and add a new SSH key to your account, paste the key into the Key field. 

### To set your global username/email configuration:  
Open the command line.  
Set your username:  
```git config --global user.name "FIRST_NAME LAST_NAME"```  
Set your email address:  
```git config --global user.email "MY_NAME@example.com"```



----
last used november 21, 2024