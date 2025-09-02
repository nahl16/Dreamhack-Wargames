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
