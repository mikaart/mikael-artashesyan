# Blog 9

Welcome to new series of Blogs. **Here** is a quick summary of things I've learned this week.

## Ransomware Debrief

Today we are talking about monitoring Ransomware, a new and very affective way for adversary to gain total access of user's data and running services, completely taking over the computer and often times a network of computers. Ransomware is able to completely shut off access to  running services and data stored on the computer/server, where adversary encrypts and often times prior exctract user data (besides crucial OS running components) and claims to provide a cypher key after they get paid. I am going to talk about some of the known Ransomware types, how they take place, and what are some things to look out for. 


### WannaCry 

![Image](https://github.com/mikaart/mikael-artashesyan/blob/master/wannadie.png)

WannaCrie virus/worm/ransomware is one of the biggest cybersecurity attacks that happened in the past decade. It swept the entire world, locking up critical systems all over the globe and infecting over 230,000 computers in more than 150 countries in just one day. It was successful so by exploting Eternal Blue vulnerability in Windows, which utilises SMB (Service Message Block) as an exploitation point. Usually most of the vulnerabilities have some way of exploitation in order to grant the executable certain rights during the execution. 

Unlike locker ransomware (which locks targets out of their device so they are unable to use it), crypto-ransomware only encrypts the data on a machine, making it impossible for the affected user to access it. This is what WannaCrie does: it takes the vistims' files in lock which can be restored by a backup or by possibly paying the threat actor a ransom (which isn't recommended)

### Ransmoware behavior

While ransomware is one of the most common forms of attacks on current networks, there are still ways that we can identify the ransomware in time, before it the execution command is sent from C&C server (Command and Control). 

Since it takes time for malware to execute, the attacker will use this time to recon and collect as much information and data from the computer and the network the computer is located on. This lateral movement can easily be identified with certain security modules in tact, such as IDS or IPS, possibly collecting logs or setting alerts for using priveleged accounts around the network/time correlation of users, things that can possibly point to the adversary's activity. A lot of times ransomware attackers will also export the data stored before encrypting it, this way they can utilize and have another way of setting a ransom against the user, especially considering the data such of PII or HIPAA types.



