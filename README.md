# ActiveDirectoryProject

## Part 1: Windows Server 2025 Domain Controller Setup 🖥️ (My Lab Notes)

Here's how I set up my first **Windows Server 2025 Domain Controller (Desktop Experience)** for an AD lab:

🔄 **Started** by booting the Server 2025 ISO, selected **Windows Server 2025 Standard (Desktop Experience)** for the GUI version, and did a custom install that auto-sets up recovery partitions before a few restarts.

⚙️ **Housekeeping** with `sconfig`: **static IP** (use your DHCP address), **left DNS blank** 🔄 (DC promotion handles it), renamed to **DC01**, restarted, verified with `ipconfig /all`.

📦 **Added** AD Domain Services + DNS roles via Server Manager, then **promoted** to create my forest (**asaretech.net**) 🌳. Ignored the DNS delegation warning ⚠️ (normal for first DC), set DSRM password, accepted defaults, waited for green checks ✅, and let it install/restart.

🔑 **Logged** back in as **ASARETECH\Administrator**—AD DS and DNS roles are running 🟢. Tools show **Active Directory Users & Computers** and **DNS Manager** ready. **First DC live!** 🚀
