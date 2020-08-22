# Learning Links
## https://www.youtube.com/watch?v=RGOj5yH7evk git tutorial
## https://www.youtube.com/watch?v=_RsP81Et12s SSH setup on mac

# Github tutorials 
1. create a repository
2. create a file in that repo
3. edit file in repo
4. check history of commit click commit
        - green means added content
        - red means deleted content

# VScode
1. get VScode
2. open folder which you want to pull repo to
3. open VScode terminal

# Git
## Initial steps
1. $ git init
2. $ git config --global user.name "Name"
3. $ git config --global user.email "github-email@gmail.com"

# SSH Link to GitHub
## Generate SSH Key
Generating a new SSH key
1. Open Terminal.

2. Paste the text below, substituting in your GitHub email address.

> $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

This creates a new ssh key, using the provided email as a label.

> Generating public/private rsa key pair.

3. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

> Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]

4. At the prompt, type a secure passphrase. For more information, see "Working with SSH key passphrases".

> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]

## Adding SSH key to ssh-agent 
Adding your SSH key to the ssh-agent
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key. When adding your SSH key to the agent, use the default macOS ssh-add command, and not an application installed by macports, homebrew, or some other external source.

1. Start the ssh-agent in the background.

>$ eval "$(ssh-agent -s)"
> Agent pid 59566

2. If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.

First, check to see if your ~/.ssh/config file exists in the default location.

>$ open ~/.ssh/config
> The file /Users/you/.ssh/config does not exist.

If the file doesn't exist, create the file.

>$ touch ~/.ssh/config

Open your ~/.ssh/config file, then modify the file, replacing ~/.ssh/id_rsa if you are not using the default location and name for your id_rsa key.

> Host *
>  AddKeysToAgent yes
>  UseKeychain yes
>  IdentityFile ~/.ssh/id_rsa

3. Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_rsa in the command with the name of your private key file.

> $ ssh-add -K ~/.ssh/id_rsa

Note: The -K option is Apple's standard version of ssh-add, which stores the passphrase in your keychain for you when you add an ssh key to the ssh-agent.

If you don't have Apple's standard version installed, you may receive an error. For more information on resolving this error, see "Error: ssh-add: illegal option -- K."

4. Add the SSH key to your GitHub account.
## Saving SSH to GitHub
1. Settings -> SSH and GPG key -> new SSH key
2. Give it a title
3. paste the key
4. confirm password


## User Computer 
1. generate SSH key
        - ssh-keygen -t rsa -b 4096 -C "email@gmail.com"
        -t = type of encryption
        -b = strength of encryption 
        -C = "github-email"
        ENTER
2. Change name of the file containing the key
3. You can enter a passphrase for your key or keep it blank
4. key saved in name of key.pub
        - with SHA256
        - RSA 4096 randomart image
5. srearch for key
        - ls | grep keyname
        - the other key is a private key
        - .pub (public key) (needs to be uploaded to github to communicate)
6. Extract content of the public key
        - cat keyname.pub (shows the content of your key)
7. Copy content of public key

# Git
## Working with git CLI commands
1. git clone "repo link"

2. ls -la (to see all the file, even hidden files in that folder)

3. git status (to view any changes) (red - modified or untracked) 

4. git add (adds to git's tracking) . (all files in the folder to be tracked and modified) *.* (all files that are not tracked by git) *.extension (start tracking only files that have that ending extention)

5. git status (green - modified and untracked file are staged)

6. git commit -m "message title" -m "message discription" (commit saves locally)

7. git push (pushes all changes to github repo) origin branch (master or other) ENTER

8. check github repo

## Working with a brand new file and github
1. move into to new folder with cd

2. add a readme file and content and save

3. git init

4. git status

5. git add .

6. git commit -m "title" -m "Description"

7. create new repo (in github)

8. copy repo link

9. git remote add orgin and (paste) repo link

10. Check all remote repo connected
        - git remote -v

11. git push -u orgin master
        -u = set upstream so that u dont need to type origin master all the time

## Working with Git Branching
1. git branch (shows all the branches)
        - press q to exit 

2. git checkout -b branch-name (new branchname)

3. git branch 

4. git checkout master (to switch between branches)

5. update Readme.md and save
        - M means modified

6. git status

7. git add file name

8. git commit -m "updated branch"

9. git diff  branch-name (compares two version of the code changes)

10. git merge branch-name (will merge changes in branch into the master)

Alternative to step 10
        - pushing that branch to github
        - and making a Pull Request

11. git checkout branch-name

12. git status

13. git push -u origin branch-name

## Making a Pull Request
### In GitHub
github will have recognized a pushed branch and provide a button for Compare & pull request

1. Click Compate & Pull Request

2. Make sure your comparing the right branch

3. give the merge a title and comment

4. Click Create pull request

5. Check comments made on your pull request
        and create your own

6. Also check all commits made, files changed

7. To make a comment based on a line of code which has changed
        - go to the like of code in files changed tab
        - click the blue plus on the left side of the line of code
        - Write a comment
        - click add a single comment
        - make sure you resolve conversation before merging

8. Click Merge Pull Request
        - add any changes in description
        - confirm merge

9. Make sure changes have taken place in the master branch in  ! code tab

10. Delete branch if not needed

### In Git
1. git checkout master (go to master branch)

2. git pull orign master (will pull all changes on master or other branches)

3. git branch (see all branches)

4. git branch -d branch-name
        - d = delete

5. git branch

Merging is not so easy in practical use as there can be merge conflicts

6. git checkout -b new-branch-name

7. update a line of code

8. git status

9. git diff

10. git commit -am "title"
        -am = means it had added and commited file however works only for modified files.

11. git checkout master
someone updates the same line of code in master

12. git branch

13. git checkout new-branch
error changes made to local file in master will be overwritten by checkout commit changes

14. git status

15. git commit -am "There"

16. git checkout new-branch

17. git diff master

18. git merge master

Conflict in index.html (usually fix it on github or terminal or code editor)

19. using code editor delete conflict markers and save change

20. git status

21. git diff

22. git commit -am "comment"

## Undoing in Git
### Undo a stage
1. git status

2. git add Readme.md

3. git status

4. git reset name-file

5. git status

### Undo a commit
1. git add filename

2. git commit -m "commit and reset"

3. git status

4. git reset HEAD~1
        - HEAD pointer to the last commit (by itself will undo commit)
        - ~1 instead of last commit it will point to the last commit further
        (thus it will undo commit and )

5. git status

6. git diff

7. git log
        - list new to old

To roll back to older commits
8. copy the commit hash

9. git reset commit-hash

10. git log

11. git reset --hard commit-hash 

## Forking
For git repo that you dont have control over and you would like to give some updates or share some info and give it yourn own updates.

1. Click the fork
2. Click your user account
3. dev
4. if you want to set it to the main repo




