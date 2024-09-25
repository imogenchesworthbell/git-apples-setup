![logo](https://user-images.githubusercontent.com/44912347/201743027-4f29bdad-8418-4d72-80f5-f2f2527add15.jpg)

# Git Collaboration
**GOAL**: In this project, you and your partner will be creating a list of apples in a text document, all version-controlled with Git!  While this project has an apples-listing theme, the apples (and the project) is not the point: The real goal is to give us an introduction to how we’ll be collaborating via Git in the coming lessons.

Collaborators: _________________

## Part 1: First Edits and `git status`
1. Open the project in VS Code.  From within your project directory, type code ., and that should open your project in VS Code.
2. Open the README and edit the line that says Collaborators: _________________ to include your names.
3. Create a new file, `apples.txt`. Add one item granny smith in it.
4. In your terminal type `git status`:
    - If it is not already, `git status` should become one of your favorite and most used git commands. It gives you a lot of information, including which branch you are on (more about branches soon), and information about the state of files that have been modified since the last commit.

5. You should see both your `README.md` and `apples.txt` files listed in red. This means they have not yet been staged to be included in the next commit. 
6. You should notice that they are listed in different sections. README.md is in a category called "Changes not staged for commit" while apples.txt is under "Untracked files". What’s the difference between “unstaged” and “untracked” files?

## Part 2: `git add`
1. Add these files to the staging area! We do this using the `git add` command. Go ahead and type `git add` in the terminal.
2. Oops! Looks like you got an error message. We have to specify which files you want to add to the staging area. There are a couple of ways to do so:
    - If you want to add only some of the modified files to the staging area, you can use the pathname of the file. This might look like `git add README.md apples.txt`
    - If you want to stage every file with changes, including untracked files, you can use `git add -A` (or the longer equivalent `git add --all`) 
    - A popular shortcut to stage all of your changes is `git add .`
3. Using any of the above methods, add `README.md` and `apples.txt` to the staging area.
4. Type `git status` you should see both files listed in green under "Changes to be committed."

## Part 3: `git commit`
1. Work together as partners to add a few apples to `apples.txt`. It doesn’t matter how many or which ones.
2. Since Partner A has been driving and Partner B has been navigating for a while, it is time to switch roles. Before Partner A commits the changes you have made, do one more `git status`. You will see that because you made changes to `apples.txt` after it was staged, you now have to add those changes to the staging area.
3. Partner A should execute the following commands to commit all of the changes you have made so far.
```bash
git add .
git commit -m "A message describing changes since the last commit" 
```

4. If you type `git status`, you should see a message saying there are no changes to commit and that your branch is 1 commit ahead of 'origin/main'.

## Part 4A: `git push`
1. **Both Partners**: Go to your personal GitHub fork of the repo. You will notice that even if you refresh the page, you will not see Partner A's commit or any of the changes you have made so far. Currently Partner A has only been making changes to their local repository.
2. **Partner A**: To see the commit in their GitHub remote, Partner A must push those changes. To do so, type the `git push` command, followed by the name of the remote you want to push changes to and then the branch to push to (in junior phase, you will almost always push to the main branch, but you can push to other branches as well).
```bash
git push origin main
```
3. **Partner A**: Type git status, you should see that your branch is up to date with 'origin/main'.
4. **Partner A**: Refresh their GitHub page again. You should now see your commit!

## Part 4B: `git pull`
1. **Partner B**: Refresh your GitHub page. Do you see Partner A’s commits? What!?! No changes. No new commits.
2. **Partner B**: To access Partner A’s work, Partner B should pull from Partner A's remote repository. Use the name you assigned to Partner A's repo when you added it as a remote. Again, we specify that we want to pull from the main branch.
```bash
git pull partner main 
// Replace "partner" with the name of your partner's branch
```
3. Type `git pull` command fetches any changes from the remote and merges them into the local branch.
4. Partner B should now see the changes Partner A made in their local repository!

## Part 5: `git log`
1. **Partner B**: Type `git log`. You should see Partner A's commit at the top of the list. This is because when you merge a branch into one you are currently in, all of the commits in the second branch since their histories diverged are incorporated into the current branch.
2. **Partner B**: Go refresh your GitHub page one more time. What happened? Why?
3. **Partner B**: What do you think you will see when Partner B types `git status`? Type git status to see if you were correct!
4. You now have two options for how to proceed. Partner B can either:
    - Push Partner A's commit to their GitHub repo before making new changes.
    - Continue working on their local repository and push both Partner A's commit and any commits they make at the same time.
5. If you choose to push the changes now, you should type the same command Partner A did a few steps ago:
```bash
git push origin main
```

## Part 6: Merge Conflicts
### Partner A: Creating a Problem
1. **Partner A**: Change the granny smith apple in your `apples.txt` to any other apple. Save it, but don’t yet commit.

### Partner B: Commit and Push
1. Discuss what you should expect to see when Partner B types `git status`. **Partner B**: Type the `git status` command. Did you see what you expected?
2. **Partner B: Commit your changes and push them up to GitHub.

### Partner A: When Pulling Doesn’t Go Smoothly
1. Partner A: Try to pull the changes from Partner B's repo.
```bash
git pull partner main
```
2. Oh no! You should be seeing an error message that local changes would be overwritten and therefore the merge is aborted. Remember when Partner A (purposefully) made changes to the repo despite being the navigator? What do you see when you do git status? Why is this problematic?

There are a number of ways you can resolve the problem you are currently experiencing. The solution you will use now is particularly helpful if you don't need to keep any of the changes you have made since your last commit (like if you accidentally edited a file).

3. Type `git stash`. Your repository should revert to your last commit. Now when you do git status you should see that your working tree is clean. You should now be able to successfully pull from Partner B's repo. Go ahead and do so now.
