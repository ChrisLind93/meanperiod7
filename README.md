### Explain basic security threads like: Cross Site Scripting (XSS), SQL Injectionand whether something similar to SQL injection is possible with NoSQL databases like MongoDB, and DOS-attacks. Explain/demonstrate ways to cope with these problems, preferably via your suggestion for a seed.

- XSS enables attackers to inject client-side scripts into web pages viewed by other users. A cross-site scripting vulnerability may be used by attackers to bypass access controls such as the same-origin policy.
  
  A way to prevent or at least limit this:
  - Encode every data that is given by a user. If data is not given by a user but supplied, encode these data.
  - Sanitize HTML markup with a library designed for the job.
  - Prevent DOM-based XSS.

- SQL Injection is an attack method where the hacker inserts malicious SQL code into a web form to gain access to resources, applications or databases.
  
  In order to prevent these types of attacks:
  - Enterprises must implement the best secure coding practices and limit web application coding privileges.
  - Reduce debugging information.
  - Test web applications regularly.

--------------------------------------------------------------------------------------------------------------------

### Explain and demonstrate ways to protect user passwords on our backend, and why this is necessary

The reason why this is necessary is that in general we only have a user with a unique name and a password as the schema for our DB.
But we also don’t want to store the passwords in clear text, so whenever we want to save a user, we salt the password and store this value to our DB. 
This also means, we have to add a special compare method to compare those passwords, so we never get our hands on the real value of the user’s password. This way we protect the endpoints.

--------------------------------------------------------------------------------------------------------------------

### Explain about password hashing, salts and the difference between bcrypt and old (not recommended) algorithms like sha1, md5 etc.

A one-way hash function is an algorithm that turns messages or text into a fixed string of digits, called the cryptographic hash value.

A one-way hash function takes variable-length input ex. A message of any length and produces a fixed length output, say 160-bits. 
This is great for protecting passwords, because we want to store passwords in a form that protects them if even if the password file itself is compromised.

The hash function ensures that, if the information is changed in any way, even by just one bit, an entirely different output value is produced.
One-way indicates that it’s almost impossible to get the original text before the hash.

In cryptography, a salt is random data that is used as an additional input to a one-way function that “hashes” a password.
The primary function of salts is to defend against dictionary attacks versus a list of password hashes.
MD5 and SHA1’s general purpose is to hash functions, designed to calculate a digest of huge amounts of data in as short time as possible.
The difference between older versions like MD5, SHA1 and bcrypt is that bcrypt is far slower.

A modern server can calculate the MD5 hash of about 330MB every second. 
If your users have passwords which are lowercase, alphanumeric and 6 characters long, you can try every single possible password of that size in about 40 seconds. 
With bcrypt instead of the server cracking a password every 40 seconds, it’d be cracked in 12 years or even not at all. 

--------------------------------------------------------------------------------------------------------------------

### Explain about JSON Web Tokens (jwt) and why they are extremely suited for a REST-based API

JSON Web Token is a JSON-based open standard for passing claims between parties in web application environment. 

The tokens are designed to be compact, URL-safe and usable especially in web browser single sign-on (SSO) context. 
JWT can be typically used to pass identity of authenticated users between an identity provider and a service provider, or any other type.
