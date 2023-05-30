# caption-test
//link github account to mac terminal

ssh-keygen -t rsa -b 4096 -C "jazmin.ramirez8@ou.edu"
cd ~/.ssh
ls
eval "$(ssh-agent -s)"

//create config file
touch config
nano config
//add the following:
Host *
 AddKeysToAgent yes
 UseKeychain yes
 IdentityFile ~/.ssh/id_rsa

 
ssh-add -K ~/.ssh/id_rsa

//copy SSH key for github
pbcopy < ~/.ssh/id_rsa.pub
