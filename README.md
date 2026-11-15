# Infraestructura Corporativa Híbrida y Continuidad de Servicios

Laboratorio práctico enfocado en administración de redes segmentadas, firewall perimetral (**pfSense**), servicios híbridos (**Windows Server** y **Linux**) y automatización operativa en **Bash** sobre **VMware Workstation**.

## Estado del Proyecto
- [ ] Fase 1: Redes virtuales en VMware Workstation y segmentación con pfSense
- [ ] Fase 2: Windows Server (AD DS, DNS, DHCP, SMB) y cliente unido al dominio
- [ ] Fase 3: Linux Server (servicio interno, hardening, backup en Bash y cron)
- [ ] Fase 4: Pruebas de validación, recuperación ante fallos y documentación final

## Estructura del Repositorio
- `docs/direccionamiento.md`: Subredes, gateways, rangos DHCP y reglas de firewall.
- `docs/guia-despliegue.md`: Pasos de configuración y decisiones técnicas.
- `docs/pruebas-recuperacion.md`: Evidencias de segmentación, permisos y restauración.
- `scripts/backup_servicio.sh`: Automatización de respaldos y verificación en Bash.