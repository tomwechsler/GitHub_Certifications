# Working with Branches

In this lab, we'll start working with branches by creating a new branch and making changes on it.

**Prerequisites**  

This lab assumes that you have done Lab 3: Working with Changes Over Time and Using Tags.  You should start out in the same directory as that lab.

**Steps**  

1. Starting in the same directory as you used for Lab 3, take a look at what branches you have currently with the git branch command.
```
git branch
```

2. You'll see a line that says "* main". This indicates that there is only one branch currently in your repository - main. The "*" next to it indicates that it is the current branch (the one you've switched to and are currently working in). If your terminal prompt is configured to show the current branch, it would also say "main".

3. Now, before we work with a new branch, let's update the files in the main branch to indicate that these are the versions on main so it will be easier to see which version we have later. To do this, we can just use a short version of the same way we have been creating and updating other files. On some non-Windows systems, run this command.
```
echo "main version" >> *
```
On Windows and some other systems, it will be necessary to issue the command for each file, such as:
```
echo "main version" >> content-file1
echo "main version" >> content-file2
```

4. Stage and commit the updated files. Because these are files that Git already knows about, we can use the shortcut command here.
```
git commit -am "main version"
```

5. (Optional) When we work with branches, it can be helpful to see a visual representation of what's in the repository. To do this, we'll use the Gitk tool that comes with Git. Start up gitk in this directory and have it run in the background.
```
gitk &
```

6. (Optional) In gitk, create a new view. Follow the instructions below.

- On the menu, select View, New View. Give it a name.
- Check "Remember this view"
- Check the four checkboxes under the "Branches & tags:" field. 4. Click OK.
- Check that the new view is now selected under the View menu. If not, select new view under that menu.

7. We have a new feature to work on, create a branch for the feature. Switch back to your terminal, and in the directory, run the command below.
```
git branch feature-branch-name
```

8. Notice that this command created the branch but did not switch to it. Let's check what branches we have and which is our current one.
```
git branch
```

9. We can now see our new branch listed. Let's change into the feature branch to do some work.
```
git checkout feature-branch-name
```

10. Verify that we're on the feature branch. Run the command below and observe that the "*" is next to that branch.
```
git branch
```

11. (Optional) Switch back to gitk, and refresh the screen to see what things look like visually now. (Note, to refresh you may need to use the "Reload" or "Update" function under the "File" menu in gitk.)

12. Back in the terminal session, create a new file and then update the files in the feature branch to indicate that they are the "feature branch version".
```
echo "some-text" > new-file
```

On other systems, it will be necessary to issue the command for each file, such as:
```
echo "feature version" >> file1-name

echo "feature version" >> file2-name
```

13. When you're done, stage and commit your changes.
```
git add .

git commit -m "feature version"
```

14. (Optional) Refresh your view in gitk and take one more look around your feature branch.

15. Switch back to the main branch.
```
git checkout main
```

16. Verify you're on the right branch.
```
git branch
```

> Note: Should have a * by main.

17. Take a look at the contents of the files and verify that they're the original ones from main.
```
cat * (or "type *" on Windows)
```

18. (Optional) Refresh (reload/update) gitk and take a look around in it.

---
## *Fantastic! Another lab... DONE!!*
---