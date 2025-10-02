# Tesis Justina
Este repositorio está dedicado al proyecto colaborativo en LaTeX de la tesis para obtener el grado de Ingeniero Mecatrónico titulada "Rediseño e implementación de manipuladores para un robot de servicio de propósito general" de la Facultad de Ingeniería UNAM.

# Guía de configuración de Sublime Text para LaTeX con TeXLive

Esta guía te ayudará a configurar Sublime Text para compilar el proyecto contenido en este repositorio utilizando TeXLive. Se asume que se realiza desde un equipo con Ubuntu como sistema operativo.

## 1. Instalar el Paquete LaTeXTools

1. Abre Sublime Text
2. Presiona `Ctrl+Shift+P` para abrir la Paleta de Comandos
3. Escribe "Install Package" y selecciona "Package Control: Install Package"
4. Espera a que se cargue la lista de paquetes, luego escribe "LaTeXTools"
5. Haz clic en LaTeXTools para instalarlo

## 2. Instalación de TeXLive

Verfica que TeXLive no esté instalado:
- Abre una terminal
- Escribe `pdflatex --version` para verificar que sea accesible
- Si no se encuentra, no lo reconocerá como un comando válido.

Para instalar desde una terminal basta escribir los siguientes comandos:

```bash
sudo apt update
sudo apt install texlive-full
```

Esta instalación suele tomar tiempo, pero provee la mayoría de paquetes e idiomas necesarios para trabajar una gran variedad de proyectos.

## 3. Instalar un visualizador de PDF

Para visualizar el PDF generado por el actual repositorio de recomienda utilizar `Zathura`. Para instalarlo se ejecuta el siguiente comando desde terminal:

```bash
sudo apt install zathura
```

## 4. Configurar LaTeXTools

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
    },

    "viewer": "zathura"
}
```

4. Guarda el archivo

## 5. Configurar el Sistema de Compilación

LaTeXTools maneja esto automáticamente, pero verifica:
- Cuando abras un archivo `.tex`, el sistema de compilación debería configurarse automáticamente a "LaTeX"
- Revisa la esquina inferior derecha de Sublime Text o ve a `Tools > Build System` y asegúrate de que "Automatic" o "LaTeX" esté seleccionado


## 6. Probar tu Configuración

1. Clona el repositorio y abre el archivo `tesis.tex`
2. Presiona `Ctrl+B`
4. El PDF debería generarse y abrirse automáticamente

## 7. Atajos de Teclado Útiles

- `Ctrl+B` / `Cmd+B`: Compilar el archivo actual
- `Ctrl+L, J`: Saltar al PDF (búsqueda hacia adelante)
- `Ctrl+L, Backspace`: Eliminar archivos temporales
- `Ctrl+L, V`: Ver PDF

## Notas Importantes

- **Nunca edites** el archivo "Settings - Default" - se sobrescribe cuando el paquete se actualiza
- Solo necesitas agregar las configuraciones que quieras **modificar** de los valores predeterminados.