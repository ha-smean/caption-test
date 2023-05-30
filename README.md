# caption-test
## link github account to mac terminal

```
ssh-keygen -t rsa -b 4096 -C "jazmin.ramirez8@ou.edu"
cd ~/.ssh
ls
eval "$(ssh-agent -s)"
```

### create config file
```
touch config
nano config
```
add the following to the file:
```
Host *
 AddKeysToAgent yes
 UseKeychain yes
 IdentityFile ~/.ssh/id_rsa
 ```

 ### add key and copy to clipboard
 ```
ssh-add -K ~/.ssh/id_rsa
pbcopy < ~/.ssh/id_rsa.pub
```
