# ActiveDirectoryProject

## Part 1: Windows Server 2025 Domain Controller Setup 🖥️

Here's how I set up my first **Windows Server 2025 Domain Controller (Desktop Experience)** for an AD lab:

## Part 1: Windows Server 2025 on VirtualBox Setup

Opened VirtualBox and created new VM named "dc" - picked Windows Server 2025 (64-bit), gave it 4GB RAM, used default disk settings.

In Settings, set clipboard/drag-drop to bidirectional, bumped processors to 4 cores, left Network Adapter 1 as NAT for internet.

Started VM, attached Server 2025 ISO, booted from it. Went through install: Next > Install now > Windows Server 2025 Data Center Evaluation (Desktop Experience) > Custom > full disk > let it restart a bunch of times.

Set admin password on first login (Ctrl+Alt+Del via Input menu), then installed Guest Additions from Devices menu - ran the AMD64 exe, next-next-finish, shut down to reboot.

After restart, opened Terminal as admin > sconfig for server config. Used ipconfig to grab current DHCP IP, set it static with same IP/subnet/gateway/DNS. Verified with ipconfig /all - DHCP off, static IP good.[file:15]

📦 **Added** AD Domain Services + DNS roles via Server Manager, then **promoted** to create my forest (**asaretech.net**) 🌳. Ignored the DNS delegation warning ⚠️ (normal for first DC), set DSRM password, accepted defaults, waited for green checks ✅, and let it install/restart.

🔑 **Logged** back in as **ASARETECH\Administrator**—AD DS and DNS roles are running 🟢. Tools show **Active Directory Users & Computers** and **DNS Manager** ready. **First DC live!** 🚀

## Part 2: Create OUs, Users & Groups 🏢

Here's how I organized my **asaretech.net** domain:

To create organizational units, I opened Server Manager > Tools > Active Directory Users and Computers, right-clicked the asaretech.net domain, and selected New > Organizational Unit. I first created four department OUs directly under the domain root: Sales, Accounting, IT, and Marketing.

Next, I created two region OUs at the root level: Region A and Region B using the same right-click > New > Organizational Unit process.

To reorganize the structure, I dragged the department OUs into their respective regions—New York and Sydney into Region A, Atlanta and Frankfurt into Region B. This was a simple drag-and-drop operation in the ADUC tree view.

For user creation, I right-clicked the target OU (New York for Mark Scott, Sydney for Helly Eagan) > New > User, entered the first name, last name, and logon name, completed the wizard, and checked "User must change password at next logon" before finishing.

I then created security groups by right-clicking each city OU under the regions—New York > New > Group, named it "Sales" and selected Security group type > OK. Repeated this for Accounting (Sydney), IT (Atlanta), and Marketing (Frankfurt).

Finally, to add users to their specific groups, I right-clicked the Sales group > Properties > Members tab > Add, searched for "Mark Scott" > OK. Did the same for the Accounting group > Properties > Members > Add "Helly Eagan" > OK.
