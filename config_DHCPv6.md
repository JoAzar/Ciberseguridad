# Configuración Segura de DHCPv6

## Parámetro: `Number of Addresses`

Este valor define la **cantidad máxima de direcciones IPv6** que el servidor DHCPv6 puede asignar dinámicamente a los clientes dentro del prefijo delegado en la LAN

---

## ✅ Valor Recomendado

- **Para redes pequeñas (hogares, oficinas chicas):** `20`

- Evita asignar más direcciones de las necesarias para **mejorar la seguridad y el control** de red

---

## ⚠️ Consideraciones

- Si el número es **muy bajo**, nuevos dispositivos podrían **quedarse sin IP**

- Si el número es **muy alto**, se **pierde control** y aumenta la posibilidad de mal uso o saturación

---

## Recomendación General

- Ajustar el número según la **cantidad de dispositivos activos** en la red

- Monitorear el uso de direcciones periódicamente

- Mantener el `Valid Lifetime` en un valor razonable para evitar direcciones colgadas por mucho tiempo

---

## Ejemplo de configuración segura

```txt
System Delegated Prefix: automático o definido
Number of Addresses: 20
Valid Lifetime: 3600 (segundos)
Enable Rapid Commit: Activado
Enable Unicast: Activado
Disable Stateless Dhcpv6: Desactivado (opcional)
```

---

Creado por Favio Joel Zalazar
