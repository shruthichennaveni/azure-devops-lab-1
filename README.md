# 🚀 Deploy a Sample Web Application on Azure Virtual Machine

This project demonstrates how to create an Azure Virtual Network, deploy a Windows Virtual Machine, install IIS Web Server, host a sample web page, and attach a data disk.

---

## 📘 **Project Architecture**
```
Azure Virtual Network (VNet)
    └── Subnet
         └── Windows Virtual Machine
               ├── IIS Web Server
               ├── Hosted Sample Website (index.html)
               └── Attached Data Disk
```

---

 **Lab Tasks**
1. Create an Azure Virtual Network (VNet)  
2. Create an Azure Windows VM  
3. Enable IIS (Internet Information Services)  
4. Host a sample web application  
5. Add a data disk to the VM  

---

 **LAB 1 — Create a Virtual Network**

### 📘 What is a VNet?
A Virtual Network allows Azure resources to communicate securely.

### 🧭 Steps:
1. Go to Azure Portal → Search **Virtual Networks**
2. Click **Create**
3. Select:
   - Resource Group: `RG-WebServerLab`
   - Name: `VNet-WebApp`
4. Under IP Addresses → Use default settings
5. Review + Create  
   
---

 **LAB 2 — Create a Windows Virtual Machine**

 What is a VM?
A Virtual Machine is a computer hosted in Azure.

### 🧭 Steps:
1. Search **Virtual Machines** → **Create**
2. Select:
   - Resource Group: `RG-WebServerLab`
   - VM Name: `VM-WebApp`
   - Image: Windows Server 2019 Datacenter
   - Size: `Standard_B1s`
   - Username: `azureuser`
3. Allow inbound ports → **RDP (3389)** and **HTTP (80)**
4. Choose:
   - VNet: `VNet-WebApp`
   - Subnet: `default-subnet`
5. Review + Create

---

# 🌐 **LAB 3 — Install IIS Web Server**

### 📘 What is IIS?
IIS is Microsoft’s web server used to host websites.

### 🧭 Steps:
1. RDP into the VM using public IP  
2. Open PowerShell (Admin)  
3. Install IIS:
   ```powershell
   Install-WindowsFeature -name Web-Server -IncludeManagementTools
   ```
4. Test in a browser:
   ```
   http://localhost
   ```
5. Test from your local machine using VM Public IP.

---

 **LAB 4 — Host a Sample Web Application**

### 🧭 Steps:
1. In VM → Go to:
   ```
   C:\inetpub\wwwroot
   ```
2. Delete `iisstart.html`
3. Create a new file: `index.html`

### Sample HTML:
```html
<html>
<head><title>My Azure Web App</title></head>
<body style="background-color:#eef;">
    <h1>Welcome to My Azure Hosted Website!</h1>
    <p>This website is hosted on an Azure Windows VM using IIS.</p>
</body>
</html>
```

4. Refresh your browser → Website is live 🎉

---

# 💽 **LAB 5 — Add and Configure a Data Disk**

### 🧭 Steps:
1. Azure Portal → Go to VM → **Disks**
2. Click **Add data disk**
3. Name: `DataDisk1`, Size: 10 GB  
4. Save  
5. RDP into VM → Open **Disk Management**
6. Initialize disk → Create New Simple Volume → Assign letter (e.g., `E:`)

---

# 📊 **Summary**

| Task | Resource | Output |
|------|----------|--------|
| 1 | Virtual Network | VNet created |
| 2 | Virtual Machine | Windows VM deployed |
| 3 | IIS | Web server installed |
| 4 | Web App | Custom `index.html` hosted |
| 5 | Data Disk | Extra disk attached |

---

# 📁 Repo Structure (Recommended)
```
azure-vm-webapp-lab/
│
├── README.md
└── images/
    ├── vnet.png
    ├── vm.png
    ├── iis-homepage.png
    ├── custom-webpage.png
    └── datadisk.png
```

---

# 📝 **Next Steps**
- Add screenshots to **/images/**
- Add Azure ARM/Bicep/Terraform (later)
- Add automation scripts

---

# ⭐ **Author**
Created by Shruthi chennaveni as part of Azure learning journey.

