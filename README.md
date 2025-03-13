# 📌 Configuración de Red en Cisco

## **1️⃣ Configuración de Routers**

### **Router Tarata**
```bash
enable
configure terminal
hostname Tarata

interface GigabitEthernet0/0/0
ip address 200.30.40.1 255.255.255.252
no shutdown

interface GigabitEthernet0/0/1
ip address 200.30.40.5 255.255.255.252
no shutdown

interface vlan 1
ip address 200.30.40.9 255.255.255.252
no shutdown

interface vlan 2
ip address 200.30.40.13 255.255.255.252
no shutdown
exit
```

---

### **2️⃣ Configuración de VLANs y Switchports**

```bash
enable
configure terminal
vlan 2
exit

interface GigabitEthernet0/1/0
switchport mode access
switchport access vlan 1
no shutdown
exit

interface GigabitEthernet0/1/1
switchport mode access
switchport access vlan 2
no shutdown
exit
```

---

### **3️⃣ Verificación de Conectividad**

#### **Mostrar interfaces activas**
```bash
show ip interface brief
```

#### **Hacer ping entre dispositivos**
```bash
ping 200.30.40.9
ping 200.30.40.13
```

✅ **Si los pings responden correctamente, la configuración es exitosa.** 🚀
