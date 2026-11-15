# Direccionamiento de Red y Segmentación — Fase 1

## Topología Lógica
- **Hipervisor:** VMware Workstation Pro
- **Firewall / Router:** pfSense CE (`pfsense-lab.corp.local`)
- **Enfoque:** Segmentación por rol y mínimo privilegio entre zonas.

## Tabla de Redes
| Zona | Red VMware | Subred | Gateway | Rango DHCP | IPs Reservadas / Fijas |
| :--- | :--- | :--- | :--- | :--- | :--- |
| WAN | `VMnet8` (NAT) | DHCP externo | Automático | — | `WAN` (pfSense) |
| Gestión | `VMnet30` (Host-only) | `10.10.30.0/24` | `10.10.30.1` | `10.10.30.50–80` | `10.10.30.10` (Admin) |
| Servidores | `VMnet10` (Host-only) | `10.10.10.0/24` | `10.10.10.1` | — | `10.10.10.10` (WinSrv), `10.10.10.20` (LinuxSrv) |
| Usuarios | `VMnet20` (Host-only) | `10.10.20.0/24` | `10.10.20.1` | `10.10.20.100–200` | — |

## Reglas Base de Firewall
- **Gestión (`VMnet30`):** Acceso completo hacia `Servidores`, `Usuarios` y `WAN`.
- **Usuarios (`VMnet20`):** Bloqueo de `SSH (22)` y `RDP (3389)` hacia `Servidores` y `Gestión`; paso de `DNS (53)`, `SMB (445)`, `HTTP/HTTPS (80, 443)` y salida a `WAN`.
- **Servidores (`VMnet10`):** Salida a `WAN` para parches; bloqueo de iniciativas entrantes desde `Usuarios` fuera de puertos permitidos.