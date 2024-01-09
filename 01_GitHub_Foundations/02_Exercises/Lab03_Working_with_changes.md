# Working with Changes Over Time and Using Tags

In this lab, we'll work through some simple examples of using the Git log commands to see the flexibility it offers as well as creating an alias to help simplify using it.  We'll also look at how to tag commits to have another way to reference them.

**Prerequisites**  

This lab assumes that you have done Lab 2: Tracking Content through the File Status Lifecycle.  You should start out in the same directory as that lab.

**Steps**  

1. Starting in the same directory as you used for Lab 2, let's first make another change to the repository to make the history more interesting. Add a line to the first file you committed into the repository and then stage and commit. Note that you can use the shortcut here.
```
echo "This is a new line" >> date-file1

git commit -am "commit-message"
```

2. Now, take a look at the history we have so far in our small repository. To do this we just run the log command.
(Note: In some terminals your history may be longer than the screen and need to hit a key to continue. If you are paging through log output and want to end the listing, hit the "q" key.)
```
git log
```

3. Often when looking at Git history information, users will only want to see the first line of each entry - the "subject line". This is why it is important to make that first line meaningful in a real-life use of Git. To see only the first line of each log message, you can use the --oneline option. Try it now.
```
git log --oneline
```

4. Let's try a more complex version of the log command that includes selected pieces of history information formatted in a specific way. Be careful of your typing - note the colon after "format", the double hyphens, and the double quotes.
```
$ git log --pretty=format:"%h %ad|%s %d[%an]" --date=short
```

> Note: Press Enter to see this execute.

5. Since this is a bit much to type, let's create an alias to simplify running this command. We do this by configuring the alias name to stand for the command and its options. Enter the following, paying attention to the punctuation (double hypens, colon, vertical bars, single and double quotes, etc.) Note this command spans multiple lines - copy and paste may not work as expected.
```
git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an] ' --date=short"
```

6. Now run your new hist alias. You should see the same output as the original log command from step 3. If you encounter any problems, go back and double-check what you typed in step 4.
```
git hist
```

7. We can also use the log command (and our hist alias) on individual files. Pick one of your files and run the hist alias against it.
```
$ git hist content-file3
```

8. We're interested in seeing the differences between a couple of the revisions. But there are no version numbers. How do we pick revisions?
(Answer: We pick revisions via the SHA1 (hash) values (first 7 bytes are enough). It's the first column in the hist output.)

9. Run the git hist alias again and find the SHA1 values of the earliest and latest lines in the history.
```
git hist
```

10. We can use these SHA1 values similarly to how we might use version numbers in other systems. Let's see the history between our earliest and latest commits. To do this, we'll run the hist alias and specify the range of values using the SHA1 values. Execute the command below, substituting the appropriate SHA1 values from the history in your repository.
```
git hist earliest-SHA1..latest-SHA1
```

11. You should see a similar history as you saw previously. One thing to note here is you don't see the original (first) commit. This is because when specifying ranges via the ".." syntax, Git defines that as essentially everything after the first revision. Note that you can also run this against an individual file. Try the command below with your SHA1 values and the first file you added in the repository.
```
 git diff earliest-SHA1..latest-SHA1 file1-name
```

12. This is useful, but finding and typing SHA1 values each time for operations like this can be cumbersome. To simplify this, we can use tags to point to commits, and then use those tag names instead of the SHA1 values in commands. Let's create tags for the earliest and latest commits in our repository. We'll use the tags "first" and "last" respectively. The commands are below. Format: git tag tagname sha1-value
```
git tag first earliest-SHA1

git tag last latest-SHA1
```

13. Now that we have the tags, we can use them anyplace we used the SHA1 values before. Try out the hist alias with the tags.
```
git hist first..last
```

14. You may not have thought about it, but this is giving us the history for all of the files in the repository. This is because a tag applies to an entire commit - not a specific file in the commit. To see this more clearly, add the --name-only option to the command and run it again.
```
git hist first..last --name-only
```

15. What do we do if we only want to do an operation using a tag for one file? The answer is to simply add that filename onto the command. Try out the example below.
```
git hist first..last --name-only file1-name
```

> Note: If you are using an older version of Git, the default branch may be "master" instead of "main". If this is the case, for Labs 4 and 5, you can substitute "master" where the labs specify "main". Or you can change the default branch to main by using the command below when you are on the master branch.
```
git branch -M main
```