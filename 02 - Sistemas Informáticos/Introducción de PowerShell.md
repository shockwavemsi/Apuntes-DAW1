**PowerShell** es una herramienta multiplataforma que sirve para la automatización de tareas. Está compuesta por un shell de línea de comandos, un lenguaje de scripting y un marco de administración de configuración, y funciona en Windows, Linux y macOS.

**Tipos de comandos**:

- **Cmdlets**: Comandos que realizan acciones y devuelven objetos basados en .NET. Ejemplos: `Get-Help`, `Select-String`.
    
- **Scripts**: Secuencias de comandos que soportan variables y otras estructuras.
    
- **Programas ejecutables**: Binarios que se pueden ejecutar desde PowerShell.
    

**Cmdlets comunes**:

- `Get-Command`: Lista todos los cmdlets disponibles.
    
- `Get-Help`: Muestra la ayuda de un cmdlet.
    
- `Update-Help`: Actualiza la ayuda.
    
- `Get-Member`: Muestra propiedades, métodos y eventos de un tipo de objeto.
    
- `Get-ChildItem`: Lista el contenido de un directorio.
    
- `Get-Process`: Lista los procesos en ejecución.
    
- `Start-Sleep -Seconds 10`: Pausa de 10 segundos.
    
- `Write-Output`: Muestra un mensaje.
    
- `Read-Host`: Lee una línea de entrada de la consola.
    
- `Exit`: Termina el script o sesión.
    
- `Get-Host`: Obtiene información del host.
    

**Variables en PowerShell**:

- Las variables comienzan con `$` y no distinguen entre mayúsculas y minúsculas.
    
- Algunas variables especiales incluyen:
    
    - `$_`: Objeto del pipeline.
        
    - `$Args`: Array con los parámetros pasados.
        
    - `$?`: Estado del último comando.
        
    - `$Null`: Constante null.
        
    - `$PSVersionTable`: Versión de PowerShell.
        
    - `$Pwd`: Ruta actual.
        
    - `$Errors`: Array con los últimos errores.
        

**Uso de comillas**:

- Comillas dobles (`"`): Permiten texto e interpretación de variables.
    
- Comillas simples (`'`): Texto literal.
    
- Acento grave (``): Carácter de escape.
    

**Tipos de datos**:

- Ejemplos de tipos de variables: `[int]`, `[long]`, `[string]`, `[char]`, `[byte]`, `[bool]`, `[decimal]`.
    

**Colecciones**:

- **Tablas**: Variables que contienen múltiples elementos.
    
- **Listas**: Arrays dinámicos donde se pueden añadir o eliminar elementos.
    
- **Hashes**: Listas con pares clave-valor.