#### Non Maintenance
I never got time nor motivation to work on this. As of May 2023, Google has announced Pass Keys (https://blog.google/technology/safety-security/the-beginning-of-the-end-of-the-password/) which is a better alternative to password-less. There are a few concerns with pass keys for example dependency over a physical device which may or may not be always available, dead locks due to losing the authentication device etc.

# Password Less
A Digital Signature based authentication system to provide a password less user-login experience.

A prototype for Digital Signature based authentication system.

# Digital Signature Based Authentication System
PGP like encryption programs used in signing data/files are best for authenticating purpose. Presently, the websites depend on some arbitrary signing procedures like username-password combinations or otp sent in email or sms which are not actually a true signature. Digital Signature based Authentication System aims to provide a true method of signing in that is ethical and secure. 

The following model is a rough explanation of Digital Signature based Authentication System.

### Client Side Authentication
![Password Less Workflow](passwordless.png)

### Client Side Double Check Authentication
This method follows client side authentication method by checking the authenticity of POSTed unique message. This can be accomplished by signing the unique message with private key and then signature can be checked on the server side with public key. This ensures that the sign-in request to the server is untampered.

### Both Side Authentication
In this method, after the client side authentication, the server sends another encrypted message having timestamp of sign-in to confirm the sign-in (which can also be used to create authentic cookies... maybe unnecessary complexity?). The browser then decrypts the timestamp and stores the text. This ensures that the server has indeed agreed to sign-in.

### Both Side Double Check Authentication
After the both side authentication method, further security can be assured by double checking the encrypted timestamp. This can be done by signing (with private key on the server) the encrypted message and send to the browser for authenticity check. This ensures that the sign-in confirmation is untampered.

## Why Digital Signature Based Authentication System?
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
While TLS is being heavily promoted, Digital Signature Based Authentication System is only an idea. Maintainer got this idea on the first day of my work. As he work for the Haryana government on contractual basis, he was introduced to the web applications developed for the data entry operations. The worst thing was that most of these applications had passwords same as the usernames! The only reason for this was that employees cannot remember complex passwords.

Obviously complex passwords are frustrating. This is the only reason we have SSO. So far we have not found anything closer to this idea other than SSO but the maintainer is sure someone on the planet must have had this idea as well. Anyways, we committed to make this a reality and stop the lame passwords.

# Installing
Presently, the project is under development. There is nothing to install or run. You can star and watch this repo for upcoming changes and updates.

# Contributing
There are many ways you can contribute:
1. By writing the code
2. By testing
3. By writing the documentation
4. By spreading the word
5. By implementing the digital signature based authentication system.

## By writing the code
Password Less is expected to be a [web extension](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions) which is portable between multiple operating systems. The idea is to use a wrapper (most likely [GPGME](https://www.gnupg.org/software/gpgme/index.html)) to [GnuPG](https://www.gnupg.org/). You can contact the [maintainer](https://twitter.com/0xcrypto) for any assistance.

## By testing 
Since there is not much code to test right now, you can choose the other ways of contributing. As the code starts to emerge, Travis CI and unit testing for JavaScript and C along with usability testing is expected. We are also concerned about the security of the application and might start a bug bounty program sooner. If you have found a security issue, please contact the [maintainer](https://twitter.com/0xcrypto).

## By writing the documentation
You can contact the [maintainer](https://twitter.com/0xcrypto) for further information.

## By spreading the word
You can tell your friends, acquaintances and followers about this new method. If you are informing a larger audience, please don't alter the theory and meanings of "Digital Signature Based Authentication System" and "Password Less". Please note the followings before writing anything about Password Less and Digital Signature based Authentication System:

1. Password Less is not completely password less, ie. there is still a password for the PGP keys (not associated with websites/browsers).
2. There is no assurance that browsers will implement this methodology. There is a great chance that they can come up with a better strategy.
3. Password Less is just a web extension.
4. Installing Password Less will not automagically make websites go password less. The server-side logic is required to make Digital Signature Based Authentication System possible.
5. As Password Less is expected to be a web extension, only firefox can support Password Less on mobile. An iOS and Android app may be developed along with the web extension but not promised.
6. Password Less and Digital Signature Based Authentication System is not completely foolproof and does not claims to be.

## By implementing the digital signature based authentication system
Implementing so soon is discouraged. You should wait for at least beta version of this web extension so that users can actually use your authentication system. A WordPress plugin to support Digital Signature based Authentication System will be developed to provide a smoother transition for most websites. But for now, we are mostly concerned about the development of Password Less.  Demonstrating implementations are not only encouraged but appreciated as well. 
