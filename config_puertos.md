# 🔐 Recomendaciones de Seguridad en Puertos

## 🧩 Puertos HTTP comunes: 80 y 8080

### 🔸 Puerto 80 (HTTP)

- 📤 **Entrada (desde Internet hacia tu red)**

  - ❌ **Bloquear si no tenés un servidor web corriendo.**
  - ✅ **Dejar abierto solo si necesitás servir una web pública.**

- 📥 **Salida (desde tu red hacia Internet)**

- ✅ **No bloquearlo.** Algunas páginas aún redirigen desde HTTP antes de llegar a HTTPS.

---

### 🔸 Puerto 8080 (HTTP alternativo, usado por proxies o paneles web)

- 📤 **Entrada**

  - ❌ **Bloquear si no lo usás.** Muchos paneles web de administración lo usan

  - ✅ **Abrir solo si es necesario para un servicio específico.**

- 📥 **Salida**

  - ✅ Puede dejarse abierto

  - 🔍 Si querés ser más estricto, analizá si alguna app lo necesita primero

---

## ✅ Resumen

| Puerto | Entrada (desde Internet) | Salida (desde red interna) |
|--------|--------------------------|-----------------------------|
| **80**     | ❌ Bloquear si no se usa web | ✅ Mantener abierto          |
| **8080**   | ❌ Bloquear si no se usa    | ✅ o 🔍 revisar antes         |

---

## Consejo

Si querés máxima seguridad

- 🔒 **Bloqueá ambos en entrada**

- 🚪 **Dejá salida abierta** salvo que sepas exactamente qué tráfico querés evitar

---

Creado por Favio Joel Zalazar
