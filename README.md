# TesisJustina
Este repositorio está dedicado al proyecto colaborativo en LaTeX de la tesis titulada "Rediseño e implementación de un robot de servicio de propósito general orientado a RoboCup@HOME" de la Facultad de Ingeniería UNAM.

# Guía de Configuración de Sublime Text para LaTeX con TeXLive

Esta guía te ayudará a configurar Sublime Text para compilar proyectos LaTeX utilizando TeXLive.

## 1. Instalar el Paquete LaTeXTools

1. Abre Sublime Text
2. Presiona `Ctrl+Shift+P` (Windows/Linux) o `Cmd+Shift+P` (Mac) para abrir la Paleta de Comandos
3. Escribe "Install Package" y selecciona "Package Control: Install Package"
4. Espera a que se cargue la lista de paquetes, luego escribe "LaTeXTools"
5. Haz clic en LaTeXTools para instalarlo

## 2. Verificar la Instalación de TeXLive

Asegúrate de que TeXLive esté instalado correctamente y en tu PATH del sistema:
- Abre una terminal o símbolo del sistema
- Escribe `pdflatex --version` para verificar que sea accesible
- Si no se encuentra, necesitarás agregar el directorio bin de TeXLive a tu PATH

## 3. Configurar LaTeXTools

1. Ve a `Preferences > Package Settings > LaTeXTools > Settings`
2. Se abrirá una vista dividida con dos paneles:
   - **Panel izquierdo**: Configuración predeterminada (solo lectura, para referencia)
   - **Panel derecho**: Configuración de usuario (editable - aquí harás tus cambios)
3. En el panel derecho (editable), agrega la siguiente configuración:

```json
{
    "builder": "traditional",
    "builder_settings": {
        "command": ["pdflatex", "-synctex=1", "-interaction=nonstopmode"]
    }
}
```

4. Guarda el archivo

## 4. Configurar el Sistema de Compilación

LaTeXTools maneja esto automáticamente, pero verifica:
- Cuando abras un archivo `.tex`, el sistema de compilación debería configurarse automáticamente a "LaTeX"
- Revisa la esquina inferior derecha de Sublime Text o ve a `Tools > Build System` y asegúrate de que "Automatic" o "LaTeX" esté seleccionado

## 5. Configurar un Visor de PDF (Opcional pero Recomendado)

En tu configuración de LaTeXTools, especifica tu visor de PDF preferido:

**Para Windows:**
```json
{
    "builder": "traditional",
    "builder_settings": {
        "command": ["pdflatex", "-synctex=1", "-interaction=nonstopmode"]
    },
    "viewer": "sumatra"
}
```

**Para Mac:**
```json
{
    "builder": "traditional",
    "builder_settings": {
        "command": ["pdflatex", "-synctex=1", "-interaction=nonstopmode"]
    },
    "viewer": "skim"
}
```

**Para Linux:**
```json
{
    "builder": "traditional",
    "builder_settings": {
        "command": ["pdflatex", "-synctex=1", "-interaction=nonstopmode"]
    },
    "viewer": "evince"
}
```

## 6. Probar tu Configuración

1. Crea un nuevo archivo y guárdalo con extensión `.tex`
2. Agrega este contenido de prueba:
   ```latex
   \documentclass{article}
   \begin{document}
   ¡Hola Mundo!
   \end{document}
   ```
3. Presiona `Ctrl+B` (Windows/Linux) o `Cmd+B` (Mac) para compilar
4. El PDF debería generarse y abrirse automáticamente

## 7. Atajos de Teclado Útiles

- `Ctrl+B` / `Cmd+B`: Compilar el archivo actual
- `Ctrl+L, J`: Saltar al PDF (búsqueda hacia adelante)
- `Ctrl+L, Backspace`: Eliminar archivos temporales
- `Ctrl+L, V`: Ver PDF

## Solución de Problemas

Si la compilación falla:
- Revisa la salida de la consola (`` Ctrl+` `` o `View > Show Console`)
- Asegúrate de que los binarios de TeXLive estén en tu PATH
- Intenta ejecutar `pdflatex tuarchivo.tex` directamente desde la terminal para aislar el problema
- Consulta la documentación de LaTeXTools: `Preferences > Package Settings > LaTeXTools > README`

## Notas Importantes

- **Nunca edites** el archivo "Settings - Default" - se sobrescribe cuando el paquete se actualiza
- El archivo "Settings - User" (panel derecho) sobrescribe cualquier configuración predeterminada que desees cambiar
- Solo necesitas agregar las configuraciones que quieras **modificar** de los valores predeterminados.