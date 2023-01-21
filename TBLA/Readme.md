# Tree Branch Leaf Architecture
🌲 🌿

## Installation
1. Download the Windows or Linux Binaries as per your operating system<br>
2. Install Python from https://www.python.org
3. Open Command prompt or Bash and use **cd** to navigate it to the folder<br>Then type
> pip install -r requirements.txt

## Implementation
1. For user login or signup 
```python
from tbla import Authenticate

user = Authenticate("youremail@example.com", "yourpassword")
user.login() # For login old users
user.signup() # For new user creation

user.save("filepath/filename.extension")
# Use it for saving user information

```
2. For Tree Branch and Leaf Creation
(While login/signup)
```python
from tbla import Authenticate, Tree
user = Authenticate("youremail@example.com", "yourpassword")
user.login() # For login old users
user.signup() # For new user creation

myTree = Tree("Treename", "TreePassword", user.login()) # or user.signup()
myTree.add_branch("YourBranchName") # This adds branch in your tree.
# You can add n branches in your tree

#Nested Branch or Sub-Branch
myTree.branch("YourBranchName").add_branch("Another_Branch") # You can add n sub-branches in your branch as well 


#Leaf Creation
myTree.branch("Branch1").branch("Branch2").branch("Branch_n").leaf("LeafName).push("Some data that is to be kept in the leaf")

#Leaf is the smallest entity that is capable of holding data
#NOTE: You can't add leaf or branch inside a leaf
```


> This line<br>


```python
myTree = Tree("Treename", "TreePassword", user.login()) # or user.signup()
```



> will create a tree in your account with Treename and TreePassword as Treename and password.<br>
Think of it as a **database name** and **database password**

## Rules:
1. You can plant infinite trees in your garden.
2. Each Tree is, in total, capable of holding 26000 leaves+branches+sub-branches.
3. Each leaf is capable of holding not more than 9 MB data.
4. Each tree is capable of holding a maximum of 256 GB data.
