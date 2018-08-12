# Password Less
A prototype demonstrating Digital Signature based authentication system.

## Digital Signature Based Authentication System
PGP like encryption programs used in digitally signing data are best for authenticating users. Presently, websites depend on some arbitrary signing process like username-password combinations or otp sent in email or sms which acts like a digital signature but not truly is. Digital Signature based authentication system aims to provide a true method of signing in. 

![Password Less Workflow](passwordless.png)

### Why Digital Signature Based Authentication System?
There are many authentication systems out there in the wild. Most of them have many flaws:

1. Sensitive data like password is stored ([many times in plain text](http://plaintextoffenders.com/about/)) on the server.
2. One time passwords/urls sent via emails or SMS can be [intercepted](https://www.reddit.com/r/announcements/comments/93qnm5/we_had_a_security_incident_heres_what_you_need_to/) easily.
3. Passwords are primary target in phishing and in general, [social engineering](https://en.wikipedia.org/wiki/Social_engineering_(security)).
4. Even hashes of passwords are [not completely secure](https://en.wikipedia.org/wiki/MD5#Security).
5. Registration/Sign in form submissions are not actually signed ie. checkboxes and button clicks cannot be considered a true signature as there is no proof of authenticity of a checkbox being clicked actually by the user.
6. Low strength passwords can be bruteforced easily.
7. Many systems like OAuth and SSO depends on third parties.
8. App based OTP generation like Google Authenticator or two-factor authentication is subject to availability of the trusted device.

Digital Signature Based Authentication System cuts of large amount of redundant functionalities required by other authentication systems and provide a user centralized authentication method which makes sign-in and registration process a breeze for developers:

1. Since the private key and its passphrase are the only security concerns, the focus of security will be centralized over these two.
2. The only data of the user needed to be stored in the server is public key. Hence even if a website is compromised, only public key is leaked.
3. Since there is no password, social engineering can be reduced.
4. Decrypted unique messages are sent via POST by the browser which makes TLS essential. Browsers can forcefully disallow non-HTTPS websites to access public key.

## Why Digital Signature Based Authentication System is still not a reality?
While TLS is being heavily promoted, Digital Signature Based Authentication System is only an idea. I got this idea on the first day of my work. As I work for the Haryana government on contractual basis, I was introduced to the web applications developed for the data entry operations. The worst thing was that most of these applications had passwords same as the usernames! The only reason for this was that employees cannot remember complex passwords.

Obviously complex passwords are frustrating. This is the only reason we have SSO. So far I have not found anything closer to my idea other than SSO but I am sure someone on the planet must have had this idea as well. Anyways, I am committed to make this a reality and stop the lame passwords.


