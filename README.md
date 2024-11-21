# link github account to terminal (two ways)

### 1. Using gh `auth login`
To authenticate with GitHub using the `gh auth login` command, you'll need to follow these steps. This process involves installing the **GitHub CLI** (`gh`) and using it to log in to your GitHub account.

#### Step 1: **Install GitHub CLI**
If you haven't installed the GitHub CLI (`gh`) yet, you'll need to do so first. You can install it using the instructions for your operating system:

- **macOS**:  
  You can install it via Homebrew:
  ```bash
  brew install gh
  ```

- **Windows**:  
  Use the GitHub CLI installer from [GitHub CLI releases page](https://github.com/cli/cli/releases).


#### Step 2: **Authenticate using `gh auth login`**
Once GitHub CLI is installed, you can authenticate to GitHub using the `gh auth login` command. This command guides you through the login process, and it will allow you to use your GitHub account in the command line.

1. Open your terminal (command prompt or shell).
2. Type the following command to start the authentication process:
   ```bash
   gh auth login
   ```

3. Authenticate the CLI with the following method:
   - **GitHub.com**: This will authenticate you to the main GitHub site.

4. Next, choose the following authentication method:
   - **Authenticate with a web browser (OAuth)**: This is the default method, and the most common choice. You'll be prompted to open a URL in your web browser to authorize GitHub CLI.

#### Step 3: **Follow the OAuth Authentication Process (Web Browser)**
If you choose the **OAuth method**, the following steps will happen:
- The GitHub CLI will display a URL (e.g., `https://github.com/login/oauth/authorize`).
- Open this URL in your web browser.
- GitHub will ask for your permission to grant the GitHub CLI access to your account.
- After granting permission, GitHub will provide a one-time code.

#### Step 4: **Complete the Login Process**
- After obtaining the code, paste it back into your terminal where the GitHub CLI is running.
- Once you paste the code, GitHub CLI will complete the authentication process, and you'll be logged in.

#### Step 5: **Confirm Authentication**
After the login process completes, you can confirm that you're authenticated by checking your login status with:
```bash
gh auth status
```
This command will show you details about your active authentication session.

### Additional Information:

- **Authentication using `gh auth login`** will also store your authentication token locally, so you won't need to log in again unless you explicitly log out or your token expires.
- **Token Expiry**: If using OAuth or a PAT, tokens may expire after a period (unless you set them to not expire), so make sure to renew tokens as needed.
- The CLI will also ask whether you want to **select a default GitHub host** (GitHub.com or an enterprise instance) and **set up a default Git protocol** (HTTPS or SSH). You can configure it for a seamless experience.

Once authenticated, you can use GitHub CLI commands (`gh`) to manage repositories, issues, pull requests, and more directly from the command line.



----


### 2. Generate the SSH key 

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



