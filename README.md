> **Estado del proyecto:** prototipo en revisión. La geometría de los optotipos actuales NO está validada para uso clínico. Consultar el [plan maestro de normalización y pruebas](https://github.com/Nanyalbert/cartel-optotipo/issues/1) antes de modificar letras, tamaño, espaciado o calibración.

# Cartel de Optotipo · Black Óptica

## Guía de uso diario — versión 1.2

### Encender y conectar
1. En el Philips u otra TV compatible, abrí la dirección del cartel con `?view=tv`. Esperá el estado «TV lista para vincular». Si el cartel está abierto, el código de seis caracteres sigue visible en la franja inferior mientras no haya conexión.
2. En el celular abrí `?view=control`. Si no hay sincronización, aparece una **pantalla completa de aviso**; los botones del examen quedan bloqueados.
3. Comprobá que el código que figura en el celular sea el mismo que el del televisor; corregilo si es necesario.
4. Tocá **Sincronizar ahora**. El celular y la TV intercambian una confirmación de sesión. Recién cuando figure **Conectado a la TV** se habilita el control.
5. Elegí tipo de optotipo, ojo evaluado y nivel decimal. Para ojo derecho/izquierdo utilizá un oclusor físico cuando corresponda.

### ¿Qué hacer si se pierde la conexión?
- **No cierres ni reinicies la TV de entrada.** El celular muestra automáticamente un aviso grande «Control remoto sin sincronizar» y un botón **Sincronizar ahora**.
- Confirmá que en la TV aparezca un código. Ingresalo en el celular y pulsá el botón.
- Si la TV no responde, usá **Reconectar celular** en la propia TV; conserva la calibración.
- **Salir / volver a ingresar** genera un código nuevo y conserva la calibración; luego hay que escribir el código nuevo en el celular.
- **Reiniciar desde cero** borra la calibración y el código de la TV. Úsalo únicamente ante un problema persistente: implica volver a medir la pantalla.

### Significado de los estados
- **Conectado:** se recibió confirmación de comunicación; los controles están habilitados.
- **Conectando / comprobando:** no significa aún que la TV esté sincronizada.
- **Sincronizar / Desconectado:** las órdenes no se envían; hay que restablecer la sesión.

### Límites y verificación pendiente
Esta solución utiliza PeerJS/WebRTC y señalización externa, incluso cuando TV y celular comparten Wi-Fi. Los navegadores de TV pueden suspender pestañas o conexiones, y WebRTC podría no ser compatible con ciertos Philips. Las comprobaciones de código y sintaxis no sustituyen ensayos reales en el televisor ni validación clínica de los optotipos.



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
4. Ingresar una sola vez en el control el código mostrado en la TV. El navegador guarda el código y vuelve a conectarse automáticamente al abrir el control.
5. Configurar diagonal y distancia. Poner la TV en pantalla completa y confirmar físicamente la longitud de 100 mm con regla antes de visualizar optotipos. El navegador de la TV recuerda esas preferencias y abre directamente el cartel en siguientes visitas, siempre que no cambien la resolución y el tamaño de ventana.\n6. Guardar la URL con `?view=tv` como favorito en el navegador de la TV. Guardar `?view=control` en el celular o computadora.\n\n**Importante:** recordar el código y la calibración usa `localStorage`, disponible únicamente en ese navegador y perfil. No equivale a una instalación persistente en el firmware de la TV: al borrar los datos del navegador se pierde la configuración. Algunas TV no permiten abrir automáticamente un navegador al encender; el acceso de un toque depende del sistema operativo. Los cambios en navegador, zoom, modo pantalla completa o distancia física exigen recalibración. La vinculación WebRTC actual puede requerir recargar la página si el TV pierde la sesión.

## Limitaciones relevantes
**Versión de demostración, no dispositivo médico.** No utilizar para diagnósticos ni para medición/documentación clínica sin validación independiente. Las letras tipográficas no son optotipos Sloan homologados, E y C son formas aproximadas, y no se implementan íntegramente espaciado ETDRS ni requisitos ISO 8596. Astigmatismo, duocromo y Amsler son herramientas orientativas; no determinan por sí solas graduación o diagnóstico.

La sincronización usa señalización pública de PeerJS: necesita Internet, aunque ambos dispositivos estén en la misma red Wi-Fi; WebRTC puede fallar en algunas TV o redes. Probar navegador y conectividad antes de utilizar. No guarda datos de pacientes. El código de sesión no equivale a autenticación robusta. No está probado sobre modelos concretos de TV.

### Próximas fases
Calibración robusta, optotipos con geometría verificada, pruebas de visión cercana, historial técnico sin datos identificatorios, conexión Wi-Fi local mediante servidor propio y ensayos en televisores reales.


## Compatibilidad universal con televisores
Se utiliza una aplicación web en vez de una app exclusiva de una marca. En televisores Philips, Samsung, LG, Android/Google TV y dispositivos HDMI con navegador moderno, probar primero las URLs de TV y control. **No todos los navegadores de TV admiten WebRTC, PeerJS, JavaScript moderno, pantalla completa o almacenamiento persistente**, por lo que la compatibilidad debe probarse en cada modelo. En televisores incompatibles, conectar un Chromecast con navegador, Android TV box, mini PC o notebook por HDMI, manteniendo el mismo control desde el teléfono.

Para instalar en otro televisor: abrir `?view=tv`, configurar diagonal, distancia, modo de visualización y calibrar con regla. Cada televisor tiene su propia configuración guardada en su navegador; compartir pulgadas no equivale a compartir calibración.

### Condiciones para un examen seguro
Confirmar distancia real al paciente, relación de aspecto 16:9, nivel de zoom del navegador al 100 %, ajuste de imagen sin overscan, brillo uniforme, ausencia de escalado posterior y dimensiones con regla. Después de cada cambio de resolución o modo de pantalla, recalibrar. Los módulos de duocromo, astigmatismo y Amsler de esta versión no tienen validación instrumental. No interpretar los resultados como una evaluación visual completa.

## Interfaz de consultorio (actualización)
- Selector explícito **Ojo derecho (OD)**, **Ojo izquierdo (OI)** y **Ambos ojos (AO)** en el control del celular. Esta selección **no tapa físicamente el ojo**; utilizar oclusor externo cuando corresponda.
- Modos **Cartel completo**, **Fila única** y **Letra única**; el cartel completo presenta líneas decrecientes.
- Abanico astigmático con marcas angulares. Las marcas son orientativas, no reemplazan un instrumento validado.
- Interfaz más clara en móvil y pantalla del paciente blanca y sin controles distractores.

**Limitaciones:** el cartel de letras sigue usando fuentes tipográficas, no un juego verificado de optotipos Sloan ni una implementación certificada de ISO 8596/ETDRS. La fila completa puede requerir validación adicional de espaciado y ajuste físico en cada pantalla. Este prototipo no debe usarse como sustituto de una evaluación optométrica validada.
