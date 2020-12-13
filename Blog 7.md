# Blog 7

Welcome to new series of Blogs. **Here** is a quick summary of things I've learned this week.

## Kerberos Security

It is important to remember of Kerberos and its powerful ability to grant access to services and processes to users in Active Directory. With such powerfull tools in tact such as Mimikatz, Kerberos becomes a big attack vector where exploiting Golden or Silver ticket becomes adversary's holy grail. Today I want to talk a bit about what Kerberos is, what Silver ticket is, and how one can obtain the ticket and with what purpose is it done. 

### Kerberos Authentication flow 

Before going into details, here is the basic steps to authenticating that take place in the background: 

```
1a. Password converted to NTLM hash, a timestamp is encrypted with the hash and sent to the KDC as an authenticator in the authentication ticket request .
1b. The Domain Controller checks user information (logon restrictions, group membership, etc) & creates Ticket-Granting Ticket.

2. The TGT is encrypted, signed, & delivered to the user (AS-REP). Only the Kerberos service in the domain can open and read TGT data.

3. The User presents the TGT to the DC when requesting a Ticket Granting Service ticket. The DC opens the TGT & validates PAC checksum – If the DC can open the ticket & the checksum check out, TGT = valid. The data in the TGT is effectively copied to create the TGS ticket.

4. The TGS is encrypted using the target service accounts’ NTLM password hash and sent to the user.

5.The user connects to the server hosting the service on the appropriate port & presents the TGS. The service opens the TGS ticket using its NTLM password hash.

```
This gives us an idea of how authentication takes place. Important to notice here is that NTLM hash plays the most important role in this equation...

### What is Silver ticket

Silver ticket is obtained for services to use Kerberos by using crdential dumping technique from OS. In order to obtain one, adversary has to know a hash value for the user account that the service is runnning on. Per say, if the service targeted such as MySQL is running under a specific user account, one has to first dump the hash from the server (have initial access to it), following by manually crafting a ticket that would represent values of a normal Kerberos Ticket Granting Service. Once the Silver ticket is crafted, one can establish persistence in services, escalating further privileges and staying in the system after reboot as well. This technique is commonly known as Pass the Ticket.


