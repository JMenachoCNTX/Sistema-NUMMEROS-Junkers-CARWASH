# Sistema NUMMEROS — Junkers Car Wash

## Para qué sirve
Sistema de administración del lavadero de autos. Módulos (menú lateral):
- **Operación:** Inicio, Tablero, Registro (nueva orden de lavado con recibo), Monitoreo (8 bahías en tiempo real), Historial.
- **Caja:** Arqueo, Egresos, Aportes y devoluciones.
- **Tienda:** Venta de snacks, Inventario, Stock, Insumos de limpieza.
- **Personal:** Bonos de lavadores, Planillas (asistencia y ajustes).
- **Configuración:** Precios, Listas (clientes, tipos de vehículo, personal), Membresías (SILVER / BLACK), Equipos, Usuarios (solo admin), Mi PIN.
Roles: admin, cajero y otros con menos permisos. Login: elegir usuario + PIN de 4 dígitos.
Primera vez: si no hay usuarios, aparece un "instalador" que crea el administrador y carga precios y listas iniciales.

## Para qué empresa
JUNKERS CAR WASH (Av. Alemana entre 6to y 7mo anillo, Santa Cruz). Clientes del lavadero: JUNKERS, YANGO, externos, policía. Marca visible: "NUMMEROS by CONTAX".

## Cómo está armado (archivos principales)
- `index.html` — TODO el sistema en un solo archivo (≈2.600 líneas: HTML + CSS + JavaScript con módulos de Firebase 10). Es el archivo que se usa.
- `app.html` — restos de una primera versión; apunta a `css/base.css` y `js/app.js`, que NO existen en el repo. No funciona; no usar.
- No hay número de versión en el código; los commits se llaman "Update index.html" (subidos desde la web de GitHub).

## Dónde se guardan los datos
- **Firebase** proyecto `sistema-contax-junkers-carwash` (configuración dentro de `index.html`).
- **Authentication:** cada usuario es una cuenta de correo interna (`usuario@junkers.local`); se entra con un PIN.
- **Firestore**, colecciones: `usuarios`, `directorio` (lista de nombres para el login), `config`, `catalogos/{clientes|vehiculos|personal}/items`, `precios`, `bahias`, `ordenes`, `productos`, `movimientos`, `ventas`, `egresos`, `aportes`, `asistencia`, `planilla_ajustes`, `socios`, y membresías.
- Las reglas de seguridad de Firestore NO están en este repo (se manejan en la consola de Firebase).

## Cómo se publica
GitHub Pages: https://jmenachocntx.github.io/Sistema-NUMMEROS-Junkers-CARWASH/ (sin dominio propio, no hay `CNAME`). Cada cambio subido se publica solo.

## Cuidados importantes
- **El repositorio es PÚBLICO.** No escribir claves, PIN ni tokens en el código. (La configuración web de Firebase es pública por diseño; lo que protege los datos son las reglas.)
- **Repo duplicado:** existe otro repo, `JUNKERS-CAR-WASH`, con un solo `index.html` de prueba que no funciona (le faltan sus archivos). ESTE repo es el que está en uso. Conviene archivar o borrar el otro para no confundirse.
- Hay mejoras de seguridad pendientes en el acceso y las reglas de Firestore (Jhonny tiene el detalle aparte).
- No cambiar `DOMINIO` ni `PREFIJO` (junto a la configuración de Firebase): todos los usuarios quedarían sin poder entrar.
- No renombrar colecciones: se perderían los datos guardados.
