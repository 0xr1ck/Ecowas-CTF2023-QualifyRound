## INCREDIBLY self-referential 

```
decription : Discover my newest EC2 web service – it features an impressively self-referential element!
```

![[incredible 1.jpg]]

lets get to it, EC2-instance??  vists the site 

![[site.jpg]]

 it does  just as it says image metadata viewer web one! uploaded a jpg and fired up burp to check the response turns out it base64 encode the image 

![[burp 1.jpg]]

and yeah you guessed reverse shell but that didn't work so decided to make a quick search about EC2-metadata found this blog https://hackingthe.cloud/aws/exploitation/ec2-metadata-ssrf/ and brought everything back on sight its SSRF all this time,  submitted this http://169.254.169.254/latest/meta-data in the url passed it to repeater, check the response and yeah 

![[first bse.jpg]]

base64 decoded it in burp suite decode ```aW5mbwpzZWN1cml0eS1jcmVkZW50aWFscy```  give out this ```info, security-credentialcy``` done then submit this to the ```http://169.254.169.254/latest/meta-data/iam/security-credentials/super-secret-admin-role```  url check response and yeah base64 decode it gives us the flag  

![[final flag.jpg]]

```
flag{thats_the_most_effective_tactic_available}
```

