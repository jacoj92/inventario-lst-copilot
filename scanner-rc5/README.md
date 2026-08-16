# RC5-B3.2 — Scanner web de identificación física

## Objetivo

Validar la lectura física real de las etiquetas piloto mediante cámara de celular.

Formatos objetivo:
- QR
- Code 128

La página usa `BrowserMultiFormatReader` de ZXing Browser 0.2.1.

## Importante

Esta revisión es SOLO LECTURA LOCAL.

No:
- llama a n8n;
- consulta PostgreSQL;
- entrega bienes;
- valida devoluciones;
- cambia inventario.

Su único trabajo es:

Etiqueta -> cámara -> texto decodificado -> normalización RC5.

## Prueba esperada

### ARD-001
QR -> ARD-001
Code 128 -> ARD-001

### DHT22-002
QR -> DHT22-002
Code 128 -> DHT22-002

### ESP32-001
QR -> ESP32-001
Code 128 -> ESP32-001

## Publicación

Para usar la cámara en un celular, publique `index.html` bajo HTTPS.
GitHub Pages es adecuado para esta prueba piloto.

## Criterio de aprobación B3.2

Para al menos ARD-001:

1. Leer el QR.
2. Confirmar valor `ARD-001`.
3. Leer únicamente el Code 128, evitando que el QR entre en el encuadre.
4. Confirmar nuevamente `ARD-001`.
5. Repetir al menos con DHT22-002.

Una vez aprobado, RC5-B3.3 conectará el resultado del scanner con n8n.
