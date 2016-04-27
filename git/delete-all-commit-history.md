#Delete all commit history

1. Checkout orphan branch
>`git checkout --orphan newBranch`

2. Add all files
>`git add -A`

3. Commit
>`git commit -m "Commit Message`

4. Delete original master branch
>`git branch -D master`

5. Rename current branch to master
>`git branch -m master`

6. Update repository by force
>`git push -f origin master`


