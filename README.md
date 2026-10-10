# Portal de herramientas educativas Cuatrovientos

Actualización de 10 de octubre de 2026. Catálogo público en GitHub Pages con enlaces a seis aplicaciones en PythonAnywhere Europa. CC-feedback: https://ccfeedback.eu.pythonanywhere.com/. Las mejoras recientes de su rama `webbrowser-llm` están preparadas localmente; publicación y aceptación técnica pendientes. La migración y la inclusión en el catálogo no implican autorización institucional.

## Medidas de adecuación al RGPD

El portal no recibe notas, incorpora recursos de diseño locales y no incluye formularios, analítica ni almacenamiento de datos del alumnado. GitHub Pages puede tratar registros de IP. Cada aplicación tiene autenticación, conservación y condiciones propias; la información institucional de privacidad debe completarse y validarse. Estas medidas no constituyen una certificación de cumplimiento.

CC-feedback genera inicialmente borradores con descriptores de rúbrica seleccionados por código. Sus intervalos actuales son: nivel 1 para notas menores que 5; nivel 2 desde 5 hasta menos de 7; nivel 3 desde 7 hasta menos de 8,5; nivel 4 desde 8,5. Deben validarse estos cortes y las correspondencias entre competencias y subcompetencias. Wllama mejora únicamente las sugerencias de alumnos seleccionados, individualmente o en lote, mediante inferencia local.

Flask gestiona un panel administrativo con Google OAuth y SQLite para rúbricas, consejos y ajustes. Se comprueban correo verificado y dominio; ADMIN_USER restringe las cuentas si tiene valores concretos. Vacío o con asterisco permite todas las cuentas verificadas del dominio. La sesión trata identidad del administrador; los textos de configuración se distribuyen públicamente y no deben contener información personal. Las notas y borradores del alumnado permanecen en el navegador.

Las correcciones locales cargan el `.env` junto a `server.py`, limitan los archivos públicos para proteger secretos y SQLite y permiten cargar los recursos del iframe aislado mediante cabeceras compatibles. Deben verificarse los mapeos estáticos del despliegue. La limpieza del editor no garantiza actualmente liberar el motor; cancelar solicita abortar, pero el flujo no espera siempre a que termine. La caché propia de los pesos se elimina selectivamente. No se presume borrado de documentos, mensajes ni copias externas.

El runtime se sirve con la aplicación; Hugging Face distribuye los pesos. Google interviene en la autenticación administrativa y Gmail recibe destinatario y texto al abrir el borrador. No se usa una API externa de inferencia. El procesamiento local no garantiza anonimato ni cumplimiento automático.

[Privacidad del portal](privacidad.html) · [Privacidad de CC-feedback](https://ccfeedback.eu.pythonanywhere.com/privacidad.html)

## Flujo de funcionamiento y datos

```mermaid
flowchart TD
    P[Portal en GitHub Pages] --> C[CC-feedback en PythonAnywhere Europa]
    P --> O[Otras cinco aplicaciones educativas]
    A[Administrador] --> G[Google: correo verificado y dominio]
    G --> F[Flask: sesión y lista de administración configurada]
    F --> DB[SQLite: rúbricas, consejos y ajustes]
    DB --> R[Configuración pedagógica pública]
    C --> E[Editor aislado: identidades y notas]
    E --> V[Valoración por código y borrador inicial]
    R --> V
    V --> S[Selección docente de alumnos]
    S --> W[Wllama local: solo sugerencias]
    H[Hugging Face: descarga de pesos] --> W
    W --> D[Asociación local y revisión docente]
    V --> D
    D -->|Acción expresa| M[Gmail: destinatario y texto]
    E --> X[Borrado del editor o inactividad]
```

## Direcciones del catálogo

| Recurso | Dirección |
|---|---|
| Trasladar notas | https://trasladarnotas.eu.pythonanywhere.com/ |
| Retroalimentación de competencias clave | https://ccfeedback.eu.pythonanywhere.com/ |
| Autoevaluación de competencias clave | https://competenciasclaveauto.eu.pythonanywhere.com/ |
| Cuestionarios | https://cuestionarios4v.eu.pythonanywhere.com/acceso |
| Coevaluación de trabajos grupales | https://coevaluacionequipos.eu.pythonanywhere.com/ |
| Formador de equipos | https://formadorequipos.eu.pythonanywhere.com/ |
| Safe Exam Browser | https://safeexambrowser.org/ |

Repositorio de CC-feedback: https://github.com/cuatrovientos-ci/cc-feedback/tree/webbrowser-llm. La dirección de producción está confirmada por el mantenedor; esta actualización documental no acredita que la última revisión esté publicada.

## Actuaciones pendientes de CC-feedback

Publicar y comprobar las correcciones con las cabeceras y mapeos estáticos reales. Configurar OAuth, una clave de sesión estable y la lista autorizada; reforzar CSRF, caducidad y atributos de cookies en el panel. Validar intervalos y correspondencias de rúbrica, calidad y rendimiento de sugerencias. Corregir y probar la espera de cancelación y liberación del motor. Completar responsable, DPD, base jurídica, proveedores, conservación y autorización institucional. Las pruebas locales de Flask y navegador verifican recursos, lectura de configuración y bloqueo de archivos privados; no certifican una auditoría completa del panel ni el despliegue público.

## Requisitos antes de usar datos reales

1. Confirmar su versión realmente desplegada y superar las comprobaciones de su guía con datos ficticios.
2. Obtener autorización del centro para finalidad, personas usuarias, campos, permisos y conservación. En Cuestionarios revisar expresamente los módulos sensibles; en Formador de equipos, el uso de perfiles y la validación humana.
3. Completar la información de privacidad de la herramienta y del portal: identidad del responsable, contacto/DPD cuando corresponda, finalidades, base jurídica, proveedores/garantías, conservación y canal de derechos. Revisar también titularidad/control de GitHub Pages y sus condiciones de alojamiento.
4. Confirmar la dirección final y su aviso de privacidad; no inventar rutas ni dar por verificados los enlaces de la tabla anterior.
5. Actualizar el estado únicamente de las herramientas autorizadas y mantener la distinción respecto a las pendientes. Configurar y verificar la conservación y el borrado, incluidas las copias externas. Mantener `rel="noopener noreferrer"` en enlaces que abran otra pestaña.
6. Revisar tutoriales para que no indiquen flujos anteriores que omitan los nuevos controles.

## Publicación y verificación

Publicar únicamente `index.html`, `privacidad.html` y `assets/` en la raíz que use GitHub Pages. El directorio contiene los archivos que deben publicarse; no se ha generado un nuevo ZIP. No contiene los repositorios de aplicaciones, bases de datos ni claves. La modificación local no actualiza el sitio público: hace falta subirla al repositorio/rama que tenga configurado Pages y comprobar el despliegue.

Vista previa local: `python -m http.server 8765 --bind 127.0.0.1`, abrir `http://127.0.0.1:8765/`. No requiere compilación ni paquetes de Node. Verificar escritorio y móvil, menú, enlaces de privacidad, estados visibles y ausencia de peticiones automáticas a dominios de terceros. Repetir la comprobación bajo la ruta de proyecto de GitHub Pages; todos los recursos del sitio tienen rutas relativas.

Fuentes del aviso: [documentación de GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages) y [privacidad de GitHub](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement). El código no incorpora cookies/analítica, pero GitHub documenta registros de IP por seguridad. El plazo y las garantías aplicables a la cuenta deben confirmarse; no se deducen del HTML.
