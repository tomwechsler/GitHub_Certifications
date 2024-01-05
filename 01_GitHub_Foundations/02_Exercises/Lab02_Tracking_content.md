# Tracking Content through the File Status Lifecycle

In this lab, we'll work through some simple examples of updating files in a Local Environment and viewing the status and differences between the various levels along the way.

**Prerequisites**  

This lab assumes that you have done Lab 1: Creating and Exploring a Git Repository and Managing Content.  You should start out in the same directory as that lab.

**Steps**  

1. Starting in the same directory as you used for Lab 1, run the status command or the short form to see how it looks when you have no changes to be staged or committed.
```
git status 
or 
git status –s
```

2. Create a new file and view the status.
```
echo "New Content" > content-file3

git status 
or 
git status -s
```

> Note: Is the file tracked or untracked? Answer: It's untracked - we haven't added the initial version to Git yet.

3. Stage the file and check status
```
git add . 
or 
git add content-file3

git status
```

<details open>
Is the file tracked or untracked?  What does "Changes to be committed" mean?
(Answers: The file is now tracked - we've added the initial version to Git. "Changes to be committed" implies files exist in the Staging Area and the next step for them is to be committed into the Local Repository.)
</details>

4. Edit the same file again in your Working Directory and check the status.
```
echo "New lines added" > content-file3

git status
```

<details open>
Why do we see two?
Where is the version that's listed as "Changes to be committed"? (Working Directory, Staging Area, or Local Repository) Where is the version that's listed as "Changes not staged for commit"? (Working Directory, Staging Area, or Local Repository)

(Answers: We see two because there is one version of the same file in the Working Directory and another version in the Staging Area. The version that's listed as "Changes to be committed" is in the Staging Area. The phrase implies that this version's "next step" or "next level for promotion" is to the Local Repository via a commit. The version that's listed as "Changes not staged for commit" is in the Working Directory.  The phrase implies that this version's "next step" or "next level for promotion" is to the Staging Area, since it's currently "not staged".)
</details>

5. Do a diff between the version in the Working Directory and the version in the Staging Area.
```
git diff
```

6. Go ahead and commit and do another status check.
```
git commit -m "lines added"

git status
```

<details open>
Which version did we commit – the one in the Staging Area or the one in the Working Directory?  
(Hint: Which one is left – shows up in the status?  Note the "Changes not staged for commit" part of the status message.)
(Answer: The version in the Staging Area was the one committed. The content goes through the Staging Area and then into the Local Repository.)
</details>

7. Stage the modified file you have in your Working Directory and do a status check.
```
git add . 

git status
```


8. Edit the file in the Working Directory one more time and do a status check.
```
echo "more lines are added" > content-file3

git status
```

<details open>
At this point, we have a version of the same file in the Local Repository (the one we committed in step 6), a version in the Staging Area (the one we staged in step 7), and a version in the Working Directory (step 8).
</details>

9. Diff the version in the working area against the version in the Staging Area.
```
git diff
```

10. Diff the version in the Staging Area against the version in the Local Repository.
```
git diff --staged 
or 
git diff --cached (note the -- is a double -)
```

11. Diff the version in the working area against the version in the Local Repository (the one we committed earlier).
```
git diff HEAD
```

12. Commit using the shortcut.
```
git commit -am "lines added"
```

<details open>
Which version got committed – the one in the Working Directory or the one in the Staging Area?
(Answer: Since we used the -am shortcut, the version from the Working Directory was staged (over the previous version in the Staging Area) and then that version was committed into the Local Repository.)
</details>

13. Check the status one more time. 
```
git status
```

> Notice the output - we're back to a clean Working Directory - Git has the latest versions of everything we've updated.