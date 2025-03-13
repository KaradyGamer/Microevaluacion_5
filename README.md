# 📌 Configuración de Red en Packet Tracer

## **1️⃣ Subneteo y Planificación de Direcciones IP**

| **Ubicación**       | **Subred**             | **Rango de IPs**             | **Uso**               |
|---------------------|-----------------------|-----------------------------|------------------------|
| **Tarata - Arani** | `200.30.40.0/30`       | `200.30.40.1 - 200.30.40.2`  | Enlace entre routers  |
| **Tarata - Cliza** | `200.30.40.4/30`       | `200.30.40.5 - 200.30.40.6`  | Enlace entre routers  |
| **LAN VLAN 1**     | `200.30.40.8/30`       | `200.30.40.9 - 200.30.40.10` | Dispositivos VLAN 1   |
| **LAN VLAN 2**     | `200.30.40.12/30`      | `200.30.40.13 - 200.30.40.14`| Dispositivos VLAN 2   |

---

## **2️⃣ Configuración de Routers**

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

### **3️⃣ Configuración de VLANs y Switchports**

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

### **4️⃣ Configuración de las PCs**

#### **PC en VLAN 1**
- **IP Address:** `200.30.40.10`
- **Subnet Mask:** `255.255.255.252`
- **Default Gateway:** `200.30.40.9`

#### **PC en VLAN 2**
- **IP Address:** `200.30.40.14`
- **Subnet Mask:** `255.255.255.252`
- **Default Gateway:** `200.30.40.13`

---

## **5️⃣ Verificación de Conectividad**

### **Mostrar interfaces activas**
```bash
show ip interface brief
```

### **Hacer ping entre dispositivos**
```bash
ping 200.30.40.9
ping 200.30.40.13
```

✅ **Si los pings responden correctamente, la configuración es exitosa.** 🚀

