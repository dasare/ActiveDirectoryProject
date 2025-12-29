# ActiveDirectoryProject

## Part 1: Windows Server 2025 Domain Controller Setup 🖥️ (My Lab Notes)

Here's how I set up my first **Windows Server 2025 Domain Controller (Desktop Experience)** for an AD lab:

🔄 **Started** by booting the Server 2025 ISO, selected **Windows Server 2025 Standard (Desktop Experience)** for the GUI version, and did a custom install that auto-sets up recovery partitions before a few restarts.

⚙️ **Housekeeping** with `sconfig`: **static IP** (use your DHCP address), **left DNS blank** 🔄 (DC promotion handles it), renamed to **DC01**, restarted, verified with `ipconfig /all`.

📦 **Added** AD Domain Services + DNS roles via Server Manager, then **promoted** to create my forest (**asaretech.net**) 🌳. Ignored the DNS delegation warning ⚠️ (normal for first DC), set DSRM password, accepted defaults, waited for green checks ✅, and let it install/restart.

🔑 **Logged** back in as **ASARETECH\Administrator**—AD DS and DNS roles are running 🟢. Tools show **Active Directory Users & Computers** and **DNS Manager** ready. **First DC live!** 🚀
# Part 2: Create OUs, Users & Groups 🏢

Here's how I organized my **asaretech.net** domain:

## 2. Create Security Groups 👥
Right-click OU → New → Group

| Group Name          | Scope  | Type     | OU           |
|---------------------|--------|----------|--------------|
| Sales Security      | Global | Security | New York     |
| Accounting Security | Global | Security | Sydney       |
| IT Security         | Global | Security | Atlanta      |
| Marketing           | Global | Security | Frankfurt    |

## 3. Create Users 👤
Right-click OU → New → User  
**→ Complete wizard → Check "User must change password at next logon" ✓**

**Region A:**
- **New York OU:** Mark Scott → Sales Security member
- **Sydney OU:** Helly Eagan → Accounting Security member

**Region B:**
- **Atlanta OU:** ITAdmin → IT Security member
- **Frankfurt OU:** (Marketing users ready)

## 4. Add Users to Groups ➕
Right-click Group → Properties → Members → Add  
OR Right-click User → Add to a group

- **Sales Security:** ✅ Mark Scott  
- **Accounting Security:** ✅ Helly Eagan
- **IT Security:** ✅ ITAdmin
- **Marketing:** (users ready to assign)

## 5. Verify Structure ✅
View → Advanced Features ✓
- Domain → Regions → OUs expand properly
- Groups → Members tab populated
- Users → Member Of tab shows groups

**Lab ready**: Regional structure with users & groups assigned! 🚀
