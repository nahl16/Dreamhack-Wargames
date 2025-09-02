# Dreamhack Wargame – devtool-sources (Web Exploitation)

##  Challenge Description
The challenge provided a simple webpage with no visible input fields or interactive features.  
The description hinted at checking the browser’s developer tools to uncover hidden resources.  

The goal was to retrieve the flag in the format `DH{...}`.

---

##  Initial Analysis
Opening **DevTools** in the browser (`F12`) and checking the **Network** and **Sources** tabs, I noticed that the application was bundled using **Webpack**.  

In the **Sources** tab, there was a folder containing:
- `index.js`
- some other bundled JavaScript files
- a `main.css` file

---

##  Finding the Flag
While browsing through the Webpack source files:  
- Opening `main.css` revealed, near the bottom of the file, a **comment** containing the flag in cleartext.  

Example:
```css
/* some CSS styling */
...
/* DH{example_fake_flag_here} */

```
Solution:

The flag was obtained directly from the CSS file, without any interaction with the webpage.

Flag: DH{...}

Takeaway:

DevTools is extremely powerful for frontend analysis.

Sensitive information should never be stored in static frontend files (JavaScript, CSS, or HTML), as users can always read them.

Always enforce proper security by keeping secrets server-side.

---
