# EvenIDs



* **Logins/failed logins/lockouts**
  * 4624 - An account was successfully logged on:
    * 2 = Interactive (local console)
    * 3 = Network (SMB, etc.)
    * 7 = Unlock workstation
    * 10 = Remote Interactive (RDP)
    * 11 = Cached Interactive (cached credentials)
  * 4625 - An account failed to log on
  * 4740 — A user account was locked out
* **Account modifications:**
  * 4720 - A user account was created
  * 4722 - A user account was enabled
  * 4738 - A user account was changed
  * 4725 - A user account was disabled
  * 4726 - A user account was deleted
  * 4723 - An attempt was made to change an account’s password
  * 4724 - An attempt was made to reset an account’s password
* Group modifications
  * 4732 - A member was added to a security-enabled local group
  * 4733 - A member was removed from a security-enabled local group
  * 4728 - A member was added to a security-enabled global group
  * 4729 - A member was removed from a security-enabled global group
  * 4730 — A security-enabled global group was deleted
  * 4731 — A security-enabled global group was created
* **Kerberos:**
  * 4768 - A Kerberos authentication (TGT) was requested
  * 4769 - A Kerberos service ticket (TGS) was requested (many 4769s for different SPNs in a short time from the same user)
  * 4771 - Kerberos pre-authentication failed
  * 4772 - Kerberos service ticket request failed
  *
