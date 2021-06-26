# Version Control with Git final project solution

## Introduction
This is the how the commit graph should look like if the assignment is done according to the assignment requirement. The solution is also provided at the bottom. The solution for the assignment is done using command line.

I have done the course on Coursera and would totally recommend this cours to anyone that wants to learn about Git. The link to the course: https://www.coursera.org/learn/version-control-with-git

## Result
Commit graph when running `git log --oneline --graph --all`

```
* 1a7d7fb (HEAD -> feature2) feature 2 wip
*   0c08a5b (develop) Merge branch 'hotfix1' into develop
|\
* \   8742451 Merge branch 'release1' into develop
|\ \
| | | *   1e776c2 (tag: v1.01, master) Merge branch 'hotfix1'
| | | |\
| | | |/
| | |/|
| | * | ed7e163 fix feature 1 bug Y
| | |/
| | *   80129cf (tag: v1.00) Merge branch 'release1'
| | |\
| | |/
| |/|
| * | 15bdc60 fix feature 1 big X
|/ /
* |   704d17a Merge branch 'feature1' into develop
|\ \
| * | 0a5bccc add feature 1
| * | f931fae feature 1 wip
|/ /
* / b92bc99 add fileA.txt
|/
* 967d29c add README.md
```

# SPOILER!
I would recommend that you try to do the assignment yourself before takign a look at the solution below. Try to compare to the graph shown above to ensure that you are on the right track.

## Solution steps using command line

``` bash
git init
touch README.md
git add README.md
git commit -m "add README.md"
git checkout -b develop
touch fileA.txt
git add fileA.txt
git commit -m "add fileA.txt"
git checkout -b feature1
echo "feature 1 wip" > fileA.txt
git add fileA.txt
git commit -m "feature 1 wip"
echo "feature 1 with 2 bugs" > fileA.txt
git add fileA.txt
git commit -m "add feature 1"
git checkout develop
git merge --no-ff feature1 # Use default merge message
git branch -d feature1
git checkout -b feature2
echo "feature 2 wip" >> fileA.txt
git add fileA.txt
git commit -m "feature 2 wip"
git checkout develop
git checkout -b release1
echo "feature 1 with 1 bug" > fileA.txt
git add fileA.txt
git commit -m "fix feature 1 bug X"
git checkout master
git merge --no-ff release1 # Use default merge message
git tag v1.00
git checkout develop
git merge --no-ff release1 # Use default merge message
git branch -d release1
git checkout feature2
git rebase develop # Fix merge conflict before running next command
git add fileA.txt
git rebase --continue # Use default rebase message
git checkout master
git checkout -b hotfix1
echo "feature 1" > fileA.txt
git add fileA.txt
git commit -m "fix feature 1 bug Y"
git checkout master
git merge --no-ff hotfix1 # Use default merge message
git tag v1.01
git checkout develop
git merge --no-ff hotfix1 # Use default merge message
git branch -d hotfix1
git checkout feature2
git rebase develop # Fix merge conflict before running the next command
git add fileA.txt
git rebase --continue # Use defaulte rebase messages
```