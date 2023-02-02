# Tree Branch Leaf Architecture V 2.0
🌲 🍀

## Features
1. It's easy to learn... isn't?
2. Low latency
3. 5 layers of security and encryption
4. Lesser dependencies
5. Reduced size 
6. Included MySQL Databases
7. **It's free... Forever☺️**


## Installation
1. Download the Windows or Linux Binaries as per your operating system<br>
2. Install Python from https://www.python.org
3. Open Command prompt or Bash and use **cd** to navigate it to the folder<br>Then type
> pip install -r requirements.txt

## Implementation
1. For user login or signup 
```python
from tbla import Authentication

user = Authentication("youremail@example.com", "yourpassword")
user.login() # For login old users
user.signup() # For new user creation

user.save("filepath/filename.extension")
# Use it for saving user information

```
2. For Tree Branch and Leaf Creation
(While login/signup)
```python
from tbla import Authentication, Tree
user = Authentication("youremail@example.com", "yourpassword")
user.login() # For login old users
user.signup() # For new user creation

myTree = Tree("Treename", "TreePassword", user.login()) # or user.signup()
myTree.add_branch("YourBranchName") # This adds branch in your tree.
# You can add n branches in your tree

#Nested Branch or Sub-Branch
myTree.branch("YourBranchName").add_branch("Another_Branch") # You can add n sub-branches in your branch as well 


#Leaf Creation
myTree.branch("Branch1").branch("Branch2").branch("Branch_n").leaf("LeafName").push("Some data that is to be kept in the leaf")

#Leaf is the smallest entity that is capable of holding data
#NOTE: You can't add leaf or branch inside a leaf


#To get data from the leaf, Use leaf().get() method.
data_in_leaf = myTree.branch("Branch1").branch("Branch2").branch("Branch_n").leaf("LeafName").get()
```


> This line<br>


```python
myTree = Tree("Treename", "TreePassword", user.login()) # or user.signup()
```



> will create a tree in your account with Treename and TreePassword as Treename and password.<br>
Think of it as a **database name** and **database password**

3. For Tree authentication (with ```user.load()``` method)
```python
from tbla import Authentication, Tree
user = Authentication()
myTree = Tree("Treename", "TreePassword", user.load("filepath/filename.extension"))
# user.load() loads the file that was saved using user.save()
```

4. To remove a branch or leaf

```python
# Say, you want to remove a branch named "To Remove"
# Then, use the following code
myTree.branch("Branch1").branch("Branch2").branch("To Remove") 
# Navigate to "To delete" branch
myTree.remove_branch() # Removes the last branch i.e. "To Remove"

#To remove leaf with name "LeafName"
myTree.branch("Branch-n").leaf("LeafName").remove()
```

**Important Note**
> In order to remove any branch, first remove any other Sub-Branch and Leaf

5. To filter only branch or leaf inside any branch

```python
print(myTree.branch("Branch1").branch("Branch2").branch("Branch-n").get_branches_only()) # shows only branches


print(myTree.branch("Branch1").branch("Branch2").branch("Branch-n").get_leaves_only()) # shows only leaves


```

6. To get all the content inside the branch:

```python
myTree.branch("branch").getall()
```

7. To go back to root of the tree, 

```python
myTree.goto_root()
```
## Rules:
1. You can plant **infinite trees** in your garden. 
2. Each Tree is, in total, capable of holding **29200 (leaves+branches+sub-branches+Mysql Databases).**
3. Each leaf is capable of holding **a maximum of 170 KB data.**
4. Each tree is capable of holding **a maximum of 5 GB data.**
5. Each MySQL database is capable of holding a database of **maximum of 250 MB** (Which is enough for testing)
6. This architecture is **free for everyone** 😉

**NOTE: THIS LIBRARY IS IN ALPHA PHASE::**

<br>
ALTHOUGH IT IS UNLIKELY TO HAPPEN,
BUT YOU MAY EXPERIENCE DATA LOSSES AND ACCOUNT BANS
