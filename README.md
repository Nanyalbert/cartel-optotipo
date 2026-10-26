# Cartel de Optotipo · Black Óptica

Prototipo web independiente para mostrar optotipos en una TV y manejar las pruebas desde un segundo dispositivo.

## Funciones
- Control remoto por código de sesión de seis caracteres usando PeerJS/WebRTC.
- Letras, E direccional, Landolt C, abanico astigmático, duocromo y Amsler.
- Variaciones de tamaño logMAR, símbolo o línea, aleatorización y selección OD/OI/AO.
- Configuración de distancia de examen y diagonal de TV, más calibración manual con regla de 100 mm.
- Interfaz responsive para móvil y computadora.

## Publicar
1. En GitHub, abrir **Settings → Pages**.
2. Elegir **Deploy from a branch**, branch **main**, directorio **/(root)** y guardar.
3. Abrir la URL de Pages en TV (?view=tv) y celular (?view=control).
4. Ingresar en el control el código mostrado en la TV.
5. Configurar diagonal y distancia. Poner la TV en pantalla completa y confirmar físicamente la longitud de 100 mm con regla antes de visualizar optotipos.

## Limitaciones relevantes
**Versión de demostración, no dispositivo médico.** No utilizar para diagnósticos ni para medición/documentación clínica sin validación independiente. Las letras tipográficas no son optotipos Sloan homologados, E y C son formas aproximadas, y no se implementan íntegramente espaciado ETDRS ni requisitos ISO 8596. Astigmatismo, duocromo y Amsler son herramientas orientativas; no determinan por sí solas graduación o diagnóstico.

La sincronización usa señalización pública de PeerJS: necesita Internet, aunque ambos dispositivos estén en la misma red Wi-Fi; WebRTC puede fallar en algunas TV o redes. Probar navegador y conectividad antes de utilizar. No guarda datos de pacientes. El código de sesión no equivale a autenticación robusta. No está probado sobre modelos concretos de TV.

### Próximas fases
Calibración robusta, optotipos con geometría verificada, pruebas de visión cercana, historial técnico sin datos identificatorios, conexión Wi-Fi local mediante servidor propio y ensayos en televisores reales.
