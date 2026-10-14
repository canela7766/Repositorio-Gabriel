**P1: Abre en el navegador /, luego /hola y luego /lo-que-sea. ¿Qué respuesta vas a ver en cada una?**
**¿Por qué?**

rta: Cuando en el navegador solo pongo el dominio con / me muestra: Hola desde el servidor porque no estoy cambiando la ruta y si escribo /hola o /lo-que-sea tambien muestra: Hola desde el servidor porque aunque este cambiando la ruta no la va encontrar porque no tengo mas rutas.

**P2: Abres UNA sola página en el navegador. ¿Cuántas líneas "Llegó una petición" van a aparecer en la**
**terminal? Cuando ejecutes, lee con atención qué URL aparece en cada línea.**

rta: Aparece una sola línea: Legó una peticion GET /. 
El navegador únicamente realiza la petición directa a la URL que se ingresa en la barra de direcciones.

**P3:¿Qué responde el servidor si pides /actividades/ (con slash al final)? ¿Y /ACTIVIDADES?**

rta: Si escribo /actividades sin slash me muestra todo correctmante pero al poner /actividades/ me sale un error 404 not found. 

**Reflexion**
**Escribe tres cosas que te parecieron tediosas o frágiles al hacer el servidor a mano. Las vas a**
**comparar en el siguiente momento.**

rta: 1. Tener que actualizar cada minima cosa que haga con el git, 2.Evaluar urls con condicionales, 3.Procesar datos POST/PUT

**P4: No has programado ninguna ruta para /no-existe. ¿Qué crees que responde Express si la pides?**
**Ábrela en el navegador con las herramientas de desarrollador abiertas (F12 → pestaña**
**Red/Network) y mira el código de estado.**

rta: Me va salir error 404 

**Reflexion**
**Vuelve a tus tres cosas tediosas del Momento 1. ¿Cuáles resolvió Express? ¿Alguna sigue igual?**

rta: Si Express resolvio muchas cosas ya que gracias el se resume mucho el codigo y simplifica muchas lineas que cumplen la misma función, la que sigue igual es el 1 ya que tengo que seguir actualizando todo manualmente para que se guarde en mi github.

**P5: Comenta la línea next(); y pide / en el navegador. ¿Qué ves en el navegador? ¿Qué ves en la**
**terminal? Cuando termines, vuelve a activar next();.**

rta: Cuando pongo next en mi codigo muestra la hora a la que se ejecuto eso en mi terminal y cuando lo comento pues simplemente no me aparece nada.

**P6: Pides GET /actividades/1. La actividad con id 1 sí existe. ¿Qué código de estado y qué body vas a**
**recibir?**
**Pista para cuando ejecutes: mira lo que imprime console.log('params:', req.params). ¿El 1**
**aparece con comillas o sin comillas?**

rta: Me sale el codigo 404 y me sale este body:

{
  "nombre_completo": "Solo Nombre Actualizado"
}

El 1 aparece sin comillas.

**P7: En la versión corregida, borra la palabra return que está antes de res.status(404) y pide**
**/actividades/99. ¿Qué recibe el cliente? ¿Qué aparece en la terminal? Después vuelve a poner el**
**return.**

rta: Si le quitas el return y pides una actividad inexistente como /actividades/99, el servidor enviará el error 404 pero continuará ejecutando la línea de abajo (res.json(actividad)), intentando enviar dos respuestas para una misma petición, lo que provocará que Postman se quede cargando indefinidamente y la terminal muestre un error crítico del tipo ERR_HTTP_HEADERS_SENT.

**P8: Predice el resultado de estas tres peticiones: ?tipo=agua, ?tipo=AGUA y ?tipo=fuego. Para la**
**última: ¿debería responder 404 o 200 con una lista vacía? Defiende tu respuesta.**

rta: Cuando ponemos ?tipo=agua, ?tipo=AGUA y ?tipo=fuego. ?tipo=AGUA y ?tipo=fuego nos dan un error 200 con una lista vacia mientras que ?tipo=agua nos muestra una lista de id.

**P9: ¿Qué código de estado y qué body vas a recibir? ¿Qué va a imprimir console.log('Body**
**recibido:', req.body) en la terminal?**

rta: Recibimos el codigo 201 y imprime Body recibido: undefined

**P10: Haz cualquier cambio en app.js y guarda (con --watch el servidor se reinicia solo). Vuelve a pedir**
**GET /actividades. ¿Sigue estando la actividad que creaste?**

rta: Los datos se van a guardar temporalmente en el servidor pero cuando se reinicie el servidor los datos guardados se borran.

**P11: Mueve este bloque al inicio, justo después de express.json(), y pide GET /actividades. ¿Qué**
**pasa? ¿Por qué? Después regrésalo al final.**

rta: lo que sucede es que el servidor no acepta ninguna de las otras rutas ya que al colocar el 404 arriba deja de leer ya que el express lee el odigo de arriba a abajo y si el 404 esta arriba no va a seguir leyendo

**Conclusión**

rta:explicacion Express evalúa los middlewares y rutas en el orden exacto en que fueron declarados, ejecutando el siguiente bloque cuando se invoca la función next.