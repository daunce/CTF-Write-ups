# Helicoptering

Points: 50  
Beginner  
449 Solves  

Is that an Apache I overheard?

Author: hashkitten

http://34.87.217.252:30026/


```
Helicoptering
The two parts of the flag are available at the locations below:

part one
part two
Unfortunately, they are both protected by an .htaccess file:

one/.htaccess
RewriteEngine On
RewriteCond %{HTTP_HOST} !^localhost$
RewriteRule ".*" "-" [F]
    
two/.htaccess
RewriteEngine On
RewriteCond %{THE_REQUEST} flag
RewriteRule ".*" "-" [F]
    
Your job is to bypass these restrictions and view the flag files anyway. Good luck!
```

Flag: Not solved
