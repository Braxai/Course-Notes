Git : version control software for code

Github : website that hosts git

Git Basics
* clone
  * "downloading" code to local system
  * git clone URL(from repo)
* add / commit
  * "save" to local device
  * git add <file/directory>
  * git commit -m <message>
    * good practice to have clear and concise messages
* push
  * "upload" from local to repo
  * git push <location><branch>
  * git push origin
    * origin is where repo was cloned from 
* pull
  * "download" changes to local system
  * git pull <location>
    * location can be origin
* Push / Pull conflicts
  * pull before pushing again if there is a conflict
  * fix conflicts
* Reset
  * git reset --hard <commit hash>
  * git reset --hard origin

Branches
* branch
  * work on two things at the same time
  * checkout / branch
    * git checkout <branch_name>    # change branch head
    * git checkout -b <branch_name> # change and create branch
    * git branch                    # print current branch
    * git push origin branch
* merge
  * on main : git merge branch --> merge branch and main

Pull Request on Githug 
* shows conflicts

Recommended to branch for every major feature 
* add TAs as reviewer for code review in pull request

Github Desktop! 
