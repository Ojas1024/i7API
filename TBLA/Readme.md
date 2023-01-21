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

```


> This line<br>


```python
myTree = Tree("Treename", "TreePassword", user.login()) # or user.signup()
```



> will create a tree in your account with Treename and TreePassword as Treename and password.<br>
Think of it as a **database name** and **database password**

3. For 
