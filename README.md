# ansible-k8s-cluster
**Proyecto de Infraestructura como Código:** despliegue automatizado de Kubernetes v1.31 con Ansible (Control Plane + múltiples Workers + CNI Calico). Compatible con Ubuntu, Debian y derivados.

## Contenido
- [Descripción](#descripción)  
- [Requisitos](#requisitos)  
- [Instalación y uso](#instalación-y-uso)  
- [Flujo del despliegue](#flujo-del-despliegue)  
- [Compatibilidad](#compatibilidad)  
- [Licencia](#licencia)
  
---

## Descripción
Este proyecto automatiza la creación de un **cluster Kubernetes** usando **Ansible**, desde la preparación de los nodos hasta la unión de los workers, incluyendo:

- Preparación de nodos (dependencias, ajustes del sistema, deshabilitar swap, sysctl).  
- Inicialización del Control Plane.  
- Instalación de kubelet en el Control Plane.  
- Instalación del **CNI Calico** para red de pods.  
- Unión de múltiples **Workers** al cluster.

---

## Requisitos
- Ubuntu Server o Debian (derivados compatibles)    
- **Ansible >= 2.10**  
- Acceso SSH a todos los nodos  
- Permisos de sudo en los nodos  

---


## Instalación y uso
1. Clonar el repositorio:
```bash
git clone git@github.com:antonioleonsilva/ansible-k8s-cluster.git
cd ansible-k8s-cluster
```
2. Revisar y modificar inventory/hosts.ini según tus nodos.

3. Ejecutar el playbook
```bash
ansible-playbook -i inventory/hosts.ini main.yaml
```
---

## Flujo del despliegue

1. Preparación de nodos → dependencias, swap, sysctl...
2. Inicialización del Control Plane → kubeadm init
3. Instalación de kubelet en Control Plane
4. Instalación de Calico CNI
5. Unión de Workers al cluster → kubeadm join

---

## Compatibilidad

- Ubuntu Server 20.04 / 22.04
- Debian 11 / 12
- Derivados compatibles con los repos oficiales de Kubernetes

---

## Licencia

Este proyecto está bajo la **MIT License**.  
Ver archivo [LICENSE](LICENSE) para más detalles.


