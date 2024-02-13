
# Configuring the repository

In this section, you will learn how to configure the github repository in Colab. This will be useful to upload and follow your code up.
First, you will have to create an account in [github](https://github.com/) in case you don't have an account. Otherwise, you can jump to step 1

**NOTE**: As students oyu can also apply to a pro github account. See the instructions in this [link](https://education.github.com/discount_requests/application) in case you are interested.


## Step 1: Fork the couse repository

You will have to fork the repository in order to introduce your own changes and updates. You can do this as follows: 

- Go to the [repository](https://github.com/rubenfonnegra/machine_learning) in Github, and click the fork button in the upper right corner of the page.
- Choose the owner of the repository. In case you belong to multiple organizations, choose your username. RECOMMENDED: Do not change your fork name.
- Click on "create fork".

**Note**: In case you need more information, visit this [link](https://docs.github.com/es/get-started/quickstart/fork-a-repo#propose-changes-to-someone-elses-project) 


## Step 2: Clone your forked repository.

- Go to your [Drive](https://drive.google.com/drive/u/0/my-drive), create a Colab notebook and open it.
- Mount your drive and navigate to the directory where you want to download your forked repository using the ```cd``` command.

```
%cd /content/drive/path/to/your/folder/ 
```

- Go to your fork in your github profile (github.com/<your_username>/machine_learning).
- In the upper right corner, clic in "<> Code"
- Copy the url that appears in the https section in the window. 
- Go back to your notebook and run the following command

```
!git clone https://github.com/<your_username>/machine_learning.git 
```

- Navigate inside the repository using the ```cd``` command.

```
%cd machine_learning/ 
```

**Note**: In case you need more information, visit this [link](https://docs.github.com/es/get-started/quickstart/fork-a-repo#propose-changes-to-someone-elses-project) 

## Step 3: Configure your local repository

- Move the notebook you created inside the ```Sem_1``` folder.
- Create a new section within your notebook to configure your fork.
- Again, navigate to the folders in your drive to reach the repository folder using ```cd```, and verify you are in the correct folder using ```ls```

```
%cd /content/drive/path/to/your/folder/machine_learning/
!ls
```

- Check the status of your forked repo using the ```status``` command on ```git```. As you just cloned a fresh fork, you should not see any changes in your master branch

```
!git status
```

- Configure your name and username to push changes into your fork. This must be done everytime you want to push using Colab. Once this is done, you will be ready to introduce changes into your local fork.

```
!git config --global user.email "your-email@pascualbravo.edu.co"
!git config --global user.name "Your Name or Nickname"
```

## Step 4: Configure your remote repository

- Verify you are in the correct folder using ```ls```

```
!ls 
```

- To configure your remote repository you will need to create a security access token from github to push the changes. Please follow the instructions in this [link](https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) to create your access token. Do NOT forget your token. You will see it once and will not be able to see it anymore. 

- Once you have your token, download the file ```repo_keys_sample.txt``` within the ```Sem_01``` folder and replace the value of the variable with your own token 

```
GIT_KEY=<your token here>
```

- Save the file and rename it as ```repo_keys.txt```. Then, upload it again to drive. **NOTE**: Do NOT add or update the ```repo_keys.txt``` to your repository. Consider this is an access token and your fork is public. Everybody will see your token if you update this file. Thereupon, anyone will have access to any repository or code you have stored in github. Be carefull.
- Import your key to Colab using the ```repo_private.py``` file

```
from Sem_01.repo_private import GIT_KEY
```

- In the same cell, configure your github username and repository name

```
git_token = GIT_KEY
username = "your_username"
repository = "machine_learning"
```

- Add the remote branch where you will push the changes you introduce.

```
!git remote add origin https://{git_token}@github.com/{username}/{repository}.git
```

- In case you get the error ```fatal: remote origin already exists.```, you should use the following command

```
!git remote set-url origin https://{git_token}@github.com/{username}/{repository}.git
```


## Step 5: Add changes to your fork

- Create a blank ```example.txt``` file.
- To start tracking this file to your repo use use the ```add``` command on git. You can also list multiple files and folders to start tracking or changes. In case you modify any existing file, you should add it to your repo to see the changes in the files. Only marked files with the ```add``` command will be changed in your repository. 

```
!git add example.txt
```

- Create a commit on the added file(s) and set an appropiate description.

```
!git commit -m "Adding the example.txt file" 
```

## Step 6: Push you changes into your remote forked repository

- To upload the changes into your github repository, use the push command to the branch you want to upload. 

```
!git push -u origin master
```

- Verify your changes have been updated. Go to your repository on github. It will show the last time each file was updated. Make sure your files are up-to-date.

**NOTE:** You can only update changes after commiting changes. Do NOT forget to create a commit before pushing changes to remote. Otherwise, your changes will not be uploaded.


# Updating your forked repo

This section will be useful whenever you need to update your forked repo with changes pushed in the original repository.

- First, you will have to mount your drive and access to your folder as before.


```
%cd /content/drive/path/to/your/folder/ 
```

- You should also configure your name and email

```
!git config --global user.email "your-email@pascualbravo.edu.co"
!git config --global user.name "Your Name or Nickname"
```

- You should now set the path of the original repository 

```
# Add the remote, call it "upstream":
!git remote add upstream https://github.com/rubenfonnegra/machine_learning.git
```

- Fetch the changes into your own fork repo 

```
# Fetch all the branches of that remote into remote-tracking branches
!git fetch upstream
```

- Checkout to master and rewrite all the changes

```
!git checkout master

# Rewrite your master branch so that any commits of yours that
# aren't already in upstream/master are replayed on top of that
# other branch:
!git rebase upstream/master
```

- just in case you have conflicts, you can manually either resolve or skip by using

```
!git rebase --skip
```

- Finally, push the changes into your branch

```
!git push -f origin master
```