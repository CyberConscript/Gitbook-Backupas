# New Project tasks

## Risk

You are CISO. Remote attacks 15 in the last 3 years (5 average per year) cost in total losses of 50.000$ each. You want to install a new Ultra security tool solution, which would cost 50k.$ a year. It will help to decrease almost 80% of that type of attack.\\

Risk management actions: accept, mitigate, avoid, transfer.\
Possible recommendations: purchase or not

## Identity and accounts

Business You work for has many password policy related problems. You know that some systems use outdated settings. This should be fixed. Evaluate current policies by best market practices and requestor demands:

* Password should change every month.
* Password history in line with the changes for one year.
* Password reminders
* Decent length increased +2.
* No @$^\* charracters.
* No family names, places, pets.
* Numbers allowed.

A quick list of the **NIST Password Guidelines** for easy reference:

1. No more periodic password resets
2. A defined minimum number of password characters – 8 (user-generated)
3. A defined number of characters in password at-least 64+
4. Allow special characters to be allowed, including spaces and emojis
5. A defined minimum number of password characters – 6 (system generated)
6. Avoid password hints/clues
7. Limit complexity requirements of passwords
8. Encourage 2FA/MFA and avoid SMS for 2FA
9. Avoid exposed passwords from:
   1. Previously exposed breaches
   2. Dictionary words
   3. Passwords consisting of repetitive or sequential characters
   4. Context-specific words, such as the name of the service, the username, and derivatives thereof
10. Limit failure login attempts to a definite number – 10
11. Do not truncate passwords & always store it in a one-way hash
12. Guide user and showcase the password strength through indicators
13. Store passwords securely through the use of salt and one-way hashes to prohibit password guessing attacks

Scenario: user is leaving company and he needs to be offboarded. He had amin privileges. So You must:

* Disable users Windows server access
* Change admin credentials for a specific, mission critical file server
* Evaluate network security device access, Windows AD security group access and windows Azure admin access.
