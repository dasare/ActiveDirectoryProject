# ActiveDirectoryProject

## Part 1: Windows Server 2025 Domain Controller Setup 🖥️ (My Lab Notes)

Here's how I set up my first **Windows Server 2025 Domain Controller (Desktop Experience)** for an AD lab:

🔄 **Started** by booting the Server 2025 ISO, selected **Windows Server 2025 Standard (Desktop Experience)** for the GUI version, and did a custom install that auto-sets up recovery partitions before a few restarts.

⚙️ **Housekeeping** with `sconfig`: **static IP** (use your DHCP address), **left DNS blank** 🔄 (DC promotion handles it), renamed to **DC01**, restarted, verified with `ipconfig /all`.

📦 **Added** AD Domain Services + DNS roles via Server Manager, then **promoted** to create my forest (**asaretech.net**) 🌳. Ignored the DNS delegation warning ⚠️ (normal for first DC), set DSRM password, accepted defaults, waited for green checks ✅, and let it install/restart.

🔑 **Logged** back in as **ASARETECH\Administrator**—AD DS and DNS roles are running 🟢. Tools show **Active Directory Users & Computers** and **DNS Manager** ready. **First DC live!** 🚀
# Part 2: Create OUs, Users & Groups 🏢

Here's how I organized my **asaretech.net** domain:

## Part 2: Create OUs, Users & Groups

To create organizational units, I opened Server Manager > Tools > Active Directory Users and Computers, right-clicked the asaretech.net domain, and selected New > Organizational Unit. I first created four department OUs directly under the domain root: Sales, Accounting, IT, and Marketing.

Next, I created two region OUs at the root level: Region A and Region B using the same right-click > New > Organizational Unit process.

To reorganize the structure, I dragged the department OUs into their respective regions—New York and Sydney into Region A, Atlanta and Frankfurt into Region B. This was a simple drag-and-drop operation in the ADUC tree view.

For user creation, I right-clicked the target OU (New York for Mark Scott, Sydney for Helly Eagan) > New > User, entered the first name, last name, and logon name, completed the wizard, and checked "User must change password at next logon" before finishing.

I then created security groups by right-clicking each city OU under the regions—New York > New > Group, named it "Sales" and selected Security group type > OK. Repeated this for Accounting (Sydney), IT (Atlanta), and Marketing (Frankfurt).

Finally, to add users to their specific groups, I right-clicked the Sales group > Properties > Members tab > Add, searched for "Mark Scott" > OK. Did the same for the Accounting group > Properties > Members > Add "Helly Eagan" > OK.
