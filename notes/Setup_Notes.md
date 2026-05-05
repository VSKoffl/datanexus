# Setup - Environment for the Datanexus Project
## What we set up
- `uv` — per-project package manager (like renv in R, but better)
- SSH key — passwordless authentication with GitHub
- `git init` — Git now tracks the entire datanexus/ folder
- `pyproject.toml` — project identity card, replaces requirements.txt
- Folder structure — industry standard DS project layout
## Install uv
- We use pip to install the necessary packages and they used to be installed in the global folder. We install uv so that uv sorts works like pip, but for an isolated environment
- Code : pip install uv
- Key Generation : ssh-keygen -t ed25519 -C "id@email.com" ; here ssh-keygen creates key pairs, "-t" means "type", "ed25519" is the algorithm. "-C" means "comment" which is our mail id. 
- The above code generates a couple of files out of which .pub file contains the key to be used in the git repo
- To get the key, in powershell : Get-Content ~/.ssh/id_ed25519.pub
- In Github.com, click on the profile circle icon on the right hand side top, there Settings>SSH & GPG Keys > New SSH Keys> Fill the Title, Key and  keep the mode to authenticator.
- To check or initiate connection to the repository : ssh -T git@github.com.ssh is the program that makes secure connections to remote machines. -T means "don't open an interactive terminal, just test the connection". git@github.com is the address — git is the username GitHub uses for SSH, and github.com is the server. When you typed yes at the prompt, your machine saved GitHub's fingerprint to a known_hosts file so it won't ask again.
- TO create the project : uv init datanexus
- To navigate to the projecrt directory : cd datanexus
- To initialize git : git init -b main. git init tells Git to start watching the current folder — it creates a hidden .git/ folder that stores the entire history of your project. The -b main flag sets the default branch name to main (older versions of Git default to master). From this point on, Git is tracking everything in datanexus/.
- To create any new directory within the working directory : mkdir "directory path" 
- 