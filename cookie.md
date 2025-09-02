# Dreamhack Wargame – cookie (Web Exploitation)

##  Challenge Description
The challenge provided a simple webpage that greets the user.  
The description hinted at cookies being important for authentication.  

The goal was to retrieve the flag in the format `DH{...}`.

---

##  Initial Analysis
Opening the provided source code (or checking server responses) showed that the application determines whether a user is an admin based on a cookie:

```python
username = request.cookies.get('username', None)
if username:
    greeting = f'Hello {username}, '
    if username == 'admin':
        greeting += 'flag is ' + FLAG
    else:
        greeting += 'you are not admin'
    return render_template('index.html', text=greeting)
```
---
Key Points:

The web app does not use sessions or a database.

Instead, it checks the value of a cookie named username.

If username == "admin", the flag is revealed.

## Exploitation

Start the challenge instance and open the given URL.

Open Developer Tools (F12) → go to the Console tab..

Change the value of username from guest to admin.

Run:

```
document.cookie = "username=admin; path=/";
```

Refresh the page.

The server now treats you as admin and displays the flag.

Solution:

After modifying the cookie, the page showed:

Hello admin, flag is DH{...}

---
