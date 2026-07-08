# os_endmoduleexam
CDAC Operating Systems Lab Exam (Complete End Module Practical)
Linux + Git + GitHub + Docker (Step-by-Step From Scratch)
This question paper is designed exactly like a CDAC practical. Everything is connected:
•	Linux → Create project 
•	Git → Version control the same project 
•	GitHub → Push project online 
•	Docker → Containerize the same project 
•	Docker Hub → Push Docker image 
No HTML/CSS/JS is used.
Only simple text files using nano.
________________________________________
Part A – Linux
Question
Create a Linux project named os_lab_project.
Inside it:
•	notes.txt 
•	commands.txt 
•	info.txt 
Perform file operations, permissions, searching, compression and display system information.
________________________________________
Step 1 Open Ubuntu Terminal
Open Ubuntu.
Terminal opens like
student@ubuntu:~$
Check current directory
pwd
Output
/home/student
________________________________________
Step 2 Create Project Folder
mkdir os_lab_project
Check
ls
Output
os_lab_project
________________________________________
Step 3 Enter Folder
cd os_lab_project
Check
pwd
Output
/home/student/os_lab_project
________________________________________
Step 4 Create Files using nano
Create notes.txt
nano notes.txt
Type
Linux Operating System
Save
Ctrl + O
Enter
Ctrl + X
________________________________________
Create commands.txt
nano commands.txt
Type
Basic Linux Commands
Save
Ctrl + O
Enter
Ctrl + X
________________________________________
Create info.txt
nano info.txt
Type
CDAC Operating Systems Lab
Save
Ctrl + O
Enter
Ctrl + X
________________________________________
Step 5 List Files
ls
Output
commands.txt
info.txt
notes.txt
Detailed list
ls -l
________________________________________
Step 6 Display File Content
cat notes.txt
Output
Linux Operating System
________________________________________
Step 7 Copy File
cp notes.txt backup_notes.txt
Check
ls
Output
backup_notes.txt
commands.txt
info.txt
notes.txt
________________________________________
Step 8 Rename File
mv info.txt details.txt
Check
ls
Output
backup_notes.txt
commands.txt
details.txt
notes.txt
________________________________________
Step 9 Create Directory
mkdir docs
Move file
mv commands.txt docs/
Check
ls 
ls docs

Output
os_lab_project
├── backup_notes.txt
├── details.txt
├── docs
│   └── commands.txt
└── notes.txt
________________________________________
Step 10 Search Word
grep Linux notes.txt
Output
Linux Operating System
________________________________________
Step 11 Count Words
wc notes.txt
________________________________________
Step 12 File Permissions
chmod 777 notes.txt
Check
ls -l
________________________________________
Step 13  create new user: sudo adduser username(eg.cdacuser)
    enter password and answer questions and press y.
    verify: id cdacuser
________________________________________
Step 14  create group: sudo groupadd groupname(eg. developers)
    verify: grep developers /etc/group

 add user to group: sudo usermod -aG developers cdacuser
    verify: groups cdacuser
Step 15 delete created user: sudo deluser cdacuser
    go back to home directory: cd..
    verify: pwd
 delete entire directory: rm -r docs
    verify: ls
remove file: rm commands.txt
find file: find . -name notes.txt
sort: sort notes.txt

Step 16 System Information
1. Username
whoami
2. Current Date
date
3. Kernel
uname -a
4. Memory
free -h
5. Disk
df -h
6. Running Processes
ps
7. running all process
ps -ef
________________________________________
Linux Part Completed
________________________________________
Part B – Git
Go inside project
cd ~/os_lab_project
________________________________________
Step 1 Check Git
git --version
If missing
sudo apt install git
________________________________________
Step 2 Configure Git
Replace with your details.
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
Verify
git config --list
________________________________________
Step 3 Initialize Repository
git init
Output
Initialized empty Git repository
________________________________________
Step 4 Check Status
git status
Shows
Untracked files
________________________________________
Step 5 Add Files
git add .
________________________________________
Step 6 Commit
git commit -m "Initial commit"
Output
3 files changed
________________________________________
Step 7 Check Log
git log
________________________________________
Step 8 Create Branch
git branch feature
View
git branch
Output
* master
feature
(or main, depending on your Git version)
________________________________________
Step 9 Switch Branch
git checkout feature
(or git switch feature)
________________________________________
Step 10 Edit File
nano notes.txt
Add
Git Branch Created
Save
Ctrl+O
Enter
Ctrl+X
________________________________________
Step 11 Commit Again
git add .
git commit -m "Updated notes"
________________________________________
Step 12 Switch Back
git checkout master
(or git checkout main if your default branch is main)
________________________________________
Step 13 Merge
git merge feature
Output
Fast-forward
________________________________________
Step 14 Clone Repository (Local Example)
Go to home directory:
cd ~
Clone the local repository:
git clone os_lab_project cloned_project
Check:
ls
You should see:
cloned_project
os_lab_project
________________________________________
GitHub Authentication (Complete)
Step 15 Create GitHub Account (if needed)
Go to the official website in firefox: GitHub 
Sign in to your account.
________________________________________
Step 16 Create a New Repository
After logging in:
1.	Click New Repository 
2.	Repository name:
os_lab_project
3.	Keep it Public 
4.	Do NOT check: 
o	Add README 
o	Add .gitignore 
o	License 
5.	Click Create Repository 
GitHub will display the repository URL, e.g.:
https://github.com/yourusername/os_lab_project.git
Replace yourusername with your GitHub username in the commands below.
________________________________________
Step 17 Generate Personal Access Token (PAT)
1.	Click your profile picture → Settings 
2.	Go to Developer settings 
3.	Select Personal access tokens → Tokens (classic) (or Fine-grained tokens if instructed by your institute) 
4.	Click Generate new token 
5.	Give it a name (e.g., CDAC Lab) 
6.	Set an expiry date 
7.	Select at least the repo permission (for classic tokens) 
8.	Click Generate token 
9.	Copy the token immediately and keep it safe. You won't be able to view it again. 
________________________________________
Step 18 Add Remote Repository
Go back to your project:
cd ~/os_lab_project
Add the remote:
git remote set-url origin https://pasteyourtoken@github.com/githubusername/github repo_name
Verify:
git remote -v
Output:
origin  https://github.com/yourusername/os_lab_project.git (fetch)
origin  https://github.com/yourusername/os_lab_project.git (push)
________________________________________
Step 19 Rename Branch (if needed)
Many GitHub repositories use main as the default branch.
git branch -M main
________________________________________
Step 20 Push to GitHub
git push  origin main
When prompted:
Username:
your GitHub username
Password:
Paste your Personal Access Token (PAT) (it will not be visible while typing).
If successful, you'll see messages similar to:
Enumerating objects...
Counting objects...
Writing objects...
To https://github.com/yourusername/os_lab_project.git
 * [new branch] main -> main
Branch 'main' set up to track 'origin/main'
________________________________________
Step 21 Verify on GitHub
Refresh your repository page on GitHub.
You should see your uploaded project files, commit history, and branch.
________________________________________
Part C – Docker
Use the same os_lab_project.
Step 1 Install Docker (if not installed)
sudo apt update
sudo apt install docker.io
Check:
docker --version
________________________________________
Step 2 Start Docker
sudo systemctl start docker
Enable Docker at boot:
sudo systemctl enable docker
Verify:
sudo systemctl status docker
________________________________________
Step 3 Create Dockerfile
Go to the project:
cd ~/os_lab_project
Create the file:
nano Dockerfile
Type:
FROM ubuntu:latest

WORKDIR /app

COPY . /app

CMD ["bash"]
Save:
Ctrl+O
Enter
Ctrl+X
________________________________________
Step 4 Build Docker Image
sudo docker build -t oslabimage .
Verify:
sudo docker images
You should see:
oslabimage
________________________________________
Step 5 Run Container
sudo docker run -dit --name oslabcontainer oslabimage
Verify:
sudo docker ps
________________________________________
Step 6 Open Container
sudo docker exec -it oslabcontainer bash
Inside the container:
pwd
Output:
/app
List files:
ls
You should see your project files.
Exit:
exit
________________________________________
Step 7 Copy File from Container to Host
sudo docker cp oslabcontainer:/app/notes.txt copied_notes.txt
Verify:
ls
You should see:
copied_notes.txt
________________________________________
Step 8 Login to Docker Hub
Create an account if needed at Docker Hub.
Login from the terminal:
sudo docker login
Enter:
•	Docker Hub username 
•	Docker Hub password (or access token if your account uses one) 
If successful:
Login Succeeded
________________________________________
Step 9 Tag Image
Replace yourdockerhubusername with your Docker Hub username:
sudo docker tag oslabimage yourdockerhubusername/oslabimage:latest
________________________________________
Step 10 Push Image
sudo docker push yourdockerhubusername/oslabimage:latest
________________________________________
Step 12 Verify on Docker Hub
Sign in to Docker Hub and open Repositories.
You should see:
oslabimage
with the latest tag.

