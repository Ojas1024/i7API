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


