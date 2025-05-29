# 🛡️ Criptografía

La criptografía es el conjunto de elementos y técnicas que permiten la comunicación segura entre dos personas. Este conjunto se denomina colectivamente un sistema criptográfico

### Esquema general

[ Emisor ] ---[ Clave + Algoritmo Criptográfico ]---> [ Receptor ]

El emisor cifra un mensaje utilizando un algoritmo criptográfico y una clave. El receptor debe contar con un algoritmo equivalente y la misma clave o una clave relacionada para descifrar y recuperar el mensaje original.

---

## 🔐 Cifrado César

Uno de los métodos más simples de cifrado es la cifra de César. Su funcionamiento se basa en un desplazamiento del alfabeto. Si una letra del texto claro es la N-ésima del alfabeto, se reemplaza por la letra (N + K)-ésima, donde K es un entero fijo

⚠️ César utilizaba un desplazamiento de K = 3.

Ejemplo

Texto claro: ATAQUE AL AMANECER
Cifrado (K = 1): BUBRVF BM BNBODFDS

🔓 Es un método débil, ya que solo existen 26 (o 27 en español) posibles desplazamientos, por lo que puede romperse fácilmente mediante fuerza bruta

---

## 🔑 Cifrado de Vigenère

La cifra de Vigenère utiliza una pequeña clave repetida a lo largo del texto. En cada paso, el índice de la letra de la clave se suma al de la letra del texto claro para generar la letra cifrada.

Ejemplo

Clave: ABCABCABCABCABCABC
Texto claro: ATAQUE AL AMANECER
Texto cifrado: BVDRWH ACO ACPBPHDGU

🔒 Más segura que César, ya que la clave introduce variabilidad en cada letra. Sin embargo, sigue siendo vulnerable a análisis de frecuencia si la clave es corta.

---

## 🔐🔓 Cifrado RSA (Criptografía de Clave Pública)

El cifrado RSA es un sistema de clave pública que permite el intercambio seguro de información sin necesidad de compartir una clave secreta con anterioridad.

Cada usuario tiene:

- Una clave pública (P), que puede ser compartida.
- Una clave privada (S), que se mantiene en secreto.

Esquema de funcionamiento:

El emisor cifra el mensaje usando la clave pública del receptor: C = P(M)
El receptor descifra el mensaje usando su clave privada: M = S(C)

📜 Este esquema fue esbozado por Diffie y Hellman en 1976, y desarrollado formalmente por Rivest, Shamir y Adleman (RSA).

🧮 Complejidad del cálculo en RSA

--

El cifrado RSA puede implicar operaciones como calcular: M^n mod N donde M es el mensaje como un número (posiblemente representado como un arreglo de enteros de K cifras), n y N son parte de la clave pública.

🔢 Este tipo de cálculo requiere exponenciación modular, que puede realizarse eficientemente mediante el algoritmo de exponenciación rápida (por cuadrados)

Número de operaciones: Aproximadamente O(log n) multiplicaciones modulares

⚙️ Si el exponente n tiene b bits, se necesitan en el orden de b multiplicaciones

Para claves RSA de 2048 bits, esto implica cientos de operaciones, pero sigue siendo eficiente con computadoras modernas
