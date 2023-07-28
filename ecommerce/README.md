# cookie consent
```html
   
       <div id="cookie-warning" class="cookie-warning">
        <p>This site uses cookies. By continuing to browse the site, you are agreeing to our use of cookies. <a
                href="privacy-policy.html">Learn more</a></p>
        <button id="cookie-accept">Got it!</button>
    </div>
```
# css

```css
.cookie-warning {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background-color: #f8f8f8;
  padding: 10px;
  text-align: center;
  z-index: 9999;
  box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.2);
}

.cookie-warning p {
  margin: 0;
  font-size: 14px;
}

.cookie-warning a {
  color: #333;
  text-decoration: underline;
}

.cookie-warning button {
  background-color: #333;
  color: #fff;
  border: none;
  padding: 8px 16px;
  font-size: 14px;
  cursor: pointer;
}

.cookie-warning button:hover {
  background-color: #555;
}

```
# javascript
```js
// Check if the user has already accepted the cookie
if (document.cookie.indexOf("cookieAccepted=true") === -1) {
  var cookieWarning = document.getElementById("cookie-warning");
  var cookieAcceptBtn = document.getElementById("cookie-accept");

  // Display the cookie warning
  cookieWarning.style.display = "block";

  // Handle the cookie acceptance
  cookieAcceptBtn.addEventListener("click", function() {
    // Set the cookie expiry to 365 days from now
    var expiryDate = new Date();
    expiryDate.setDate(expiryDate.getDate() + 365);

    // Set the cookie
    document.cookie = "cookieAccepted=true; expires=" + expiryDate.toUTCString();

    // Hide the cookie warning
    cookieWarning.style.display = "none";
  });
} else {
  // If the user has already accepted, hide the cookie warning
  var cookieWarning = document.getElementById("cookie-warning");
  cookieWarning.style.display = "none";
}

```