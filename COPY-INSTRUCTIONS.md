# AVM Copy Instructions

1) Git Clone AVM 

2) Remove Git History 

   - Remove the existing .git directory (this deletes all history)
   Remove-Item -Recurse -Force .git

   - Initialize a new git repository
   git init

   - Add all current files
   git add .

   - Create the initial commit
   git commit -m "Initial commit"

3) Push to a new repo
   - Add your new GitHub repository as remote (replace with your actual repo URL)
   git remote add origin https://github.com/[repo]

   - Push to the new repository
   git branch -M main
   git push -u origin main

4) Remove hard-coded references to old repo

- Use GitHub Copilot Agent mode to get help with replacements 