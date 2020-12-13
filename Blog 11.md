# Blog 11

Welcome to new series of Blogs. **Here** is a quick summary of things I've learned this week.

## Pass the Hash

A Pass-the-Hash (PtH) attack is a technique whereby an attacker captures a password hash and uses it to pass through to the recieving authenticator for potential lateral access to the network systems. Pass the hash (PtH) is a method of authenticating as a user without having access to the user's cleartext password. It bypasses standard authentication steps that require a cleartext password, moving directly into the portion of the authentication that uses password hash. Here we are gonna talk about methods of preventing such attack, as it can commonly be used on older systems of Windows and Linux. 

### Mitigation

There is a few things associated with Pass-TheHash to keepin mind. In order for pass-the-has to work, first the adversary has to gain administrative rights to retrieve the hash. Hashes can also be obtained in a leak from darkweb or elsewhere. Once they're in however, there is nothing to stop them. Here are some practices that can prevent or minimize the impact:

```
1. Least privilege - limits the scope, and mitigate the impact of the attack by reducing an attackers ability to escalate privileged access and permissions. Removing unnecessary admin rights will go a long way to reducing the threat surface for PtH and many other types of attacks.

2. Password Management - make sure to rotate passwords frequently (and/or after a known credential compromise) can condense the window of time during which a stolen hash may be valid. By automating password rotation to occur after each privileged session, you can completely thwart PtH attacks, and exploits relying on password reuse.

3. Separation of privileges - separating different types of privileged and non-privileged accounts, can reduce the scope of usage for administrator accounts, and thus, reduce the risk for compromise, as well as the opportunity for lateral movement.

4. Patching - Apply patch KB2871997 to Windows 7 and higher systems to limit the default access of accounts in the local administrator group.

5. User Account Manager - Do not allow a domain user to be in the local administrator group on multiple systems.

```


### Detection

One has to audit  logon and credential use events and review for discrepancies. Unusual remote logins that correlate with other suspicious activity (such as writing and executing binaries) that may be a sign of malicious activity. NTLMv3 authentications that are not associated to a domain login and are not anonymous logins are suspicious.