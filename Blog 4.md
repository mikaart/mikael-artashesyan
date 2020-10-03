# Blog 2

Welcome to new series of Blogs. **Here** is a quick summary of things I've learned this week.

## Cyber Kill Chain

Let's talk a little more about what Cyber Kill Chain is or rather what place does it have in the industries nowadayas. This framework represents several steps to progress the attack and stands behind the idea that by neutralizing adversary on any of the steps, you are able to kill the rest of the key chain by at least partially preventing the attack from happening. When considering this framework, it relies on understanding the attacker's goals and actions, as by knowing each step of attack execution we are only then able to setup proper defense mechanisms. Let's break those down step by step and highlight some important parts.

### Exploitation

It is initial step of the attack and is best represented by an employee clicking on phishing links, accessing rogue websites, server-based exploit triggered, etc. It is on the defenders part to prevent this from happening (which can be the hardest part). 
Some actions to consider here for defense would be :
```
1. Endpoint hardeningn measures. (Admin hardening, block rules, EDR)
2. Regular volnurability scanning
3. Endpoint process auditing to determine origin of exploit
```

### Installation

This is the step after the initial trigger was activated. It means adversary gained some access and will try to establish persistence as first step to establish a stable connection to compromised object. It could be installing a webshell, create autorun keys, deploy malware as a process, etc. 
Some actions to consider here for defense would be : 
```
1. HIPS block on common instalaltion paths
2. Enpoint process auditing for abnormal file creations
3. Extract and analyze certificates of any signed exe. file
4. Understand time the malware was compiled or whether requires admin. priveleges 
```

### Command and Control

Once the attacker initiates persistance, he connects to so-called C2 infrasturcture, which is used to remotely manipulate the victim. This type of conversation usually occurs over HTTPS, DNS, or mail protocols and can be hard to suspect in action. 
Some actions to consider here for defense would be :
```
1. Require proxy connection when dealing with HTTP/S, DNS traffic
2. Proxy blocks none or uncategorized domains
3. DNS skin holing and name server poisoning
4. Open Source research to discover C2 infastructures out there
```

### Actions on objectives

At this step, intruders will go on and escalate the priveleges and do everything that will get them around the most. Starting from escalating their privileges, collecting user cred-s, conducting internal reconaissance laterally and locally, corrupting data, and etc. It is important to remember that the longer adversary has access like this, the more impact it can bring.
Some actions to consider here for defense would be :
```
1. Establish IR playbook, including executive management and communication plan
2. Detect data exfil, lateral movement, credential dumps
3. Network package capture
4. Conduct damage assesment
```

### NOW WHAT?

#### Analysis
Analysis of multiple intrusion kill chains over time draws attention to similarities and overlapping indicators. Learn to recognize and define intrusion campaigns and understand their mission objectives.

Identify patterns: what are they looking for, why are they targeting me? This will help identify how to best protect yourself from the next attack. You can’t get ahead of the threat unless you understand the campaign.

#### Resilience
Measure the effectiveness of your contermeasuers against the threats, collect the matrics and see what works the best. It is important to become agile and adapt defenses faster than the threats do.