1. Instalar Debian 12 en modo texto, sin añadir ningún DVD más y sin conectar a través de red con ningún repositorio. No instalar ningún escritorio. Al final tendremos un S.O. solo en modo texto.
   
	![[Pasted image 20250321085454.png]]
	![[Pasted image 20250321085550.png]]
	
	![[Pasted image 20250321201528.png]]
	
	![[Pasted image 20250321201436.png]]
2. Instalar Debian 12 en modo gráfico. No añadir ningún DVD pero sí añadir los repositorios en red. Instalar todos los escritorios que ofrece la instalación.
   
	![[Pasted image 20250321095658.png]]
	
	![[Pasted image 20250321200712.png]]

3. Instalar Linux Mint.
      
	![[Pasted image 20250321091341.png]]
	
	![[Pasted image 20250321091516.png]]
	
	![[Pasted image 20250321091742.png]]

4. Instalar Fedora Workstation.
   
   ![[Pasted image 20250323112051.png]]

	![[Pasted image 20250321095257.png]]
	
	![[Pasted image 20250323113613.png]]

5. Comparar las cuatro instalaciones: - Método de instalación (facilidad, usabilidad, etc.) - Escritorio. - Busca y compara las siguientes aplicaciones en cada uno de los escritorios instalados : ofimática, navegador de archivos, navegador de internet, gestor (o gestores) de paquetes, herramientas de configuración.

### **Método de instalación**

- **Debian (solo con terminal):**
    
    - **Facilidad**: Requiere conocimientos técnicos; ideal para usuarios avanzados. La interfaz es exclusivamente de texto (modo CLI - Command Line Interface).
        
    - **Usabilidad**: Es flexible pero poco intuitiva para principiantes. Necesitas entender particionado y comandos básicos.
        
- **Debian (con interfaz gráfica):**
    
    - **Facilidad**: Más fácil que con terminal, pero requiere configurar las opciones manualmente.
        
    - **Usabilidad**: Proporciona un instalador gráfico que es funcional y directo, aunque algo austero.
        
- **Linux Mint:**
    
    - **Facilidad**: Extremadamente amigable; se dirige a principiantes. Ofrece un instalador simple y claro.
        
    - **Usabilidad**: Muy intuitiva. Generalmente, todo funciona de inmediato tras instalar (soporte mejorado para hardware).
        
- **Fedora:**
    
    - **Facilidad**: Instalador gráfico moderno y claro. Es más fácil que Debian (terminal) pero algo más avanzado que Linux Mint.
        
    - **Usabilidad**: Muy profesional, con énfasis en tecnologías nuevas y estabilidad.
        

### **Escritorio**

Dependiendo de la instalación, aquí hay algunos ejemplos típicos:

- **Debian con interfaz gráfica**: GNOME (predeterminado), pero puedes elegir KDE, XFCE , entre otros que acabamos de instalar.
    
- **Linux Mint**: Cinnamon (predeterminado), MATE, XFCE.
    
- **Fedora**: GNOME predeterminado en la versión estándar.
    
- **Debian solo con terminal**: Sin entorno gráfico a menos que lo instales posteriormente.
    

### **Comparación de Aplicaciones Comunes**

| **Categoría**                     | **Debian (CLI)**                       | **Debian (Gráfica)**                       | **Linux Mint**            | **Fedora**             |
| --------------------------------- | -------------------------------------- | ------------------------------------------ | ------------------------- | ---------------------- |
| **Ofimática**                     | LibreOffice (debes instalarla)         | LibreOffice                                | LibreOffice (incluida)    | LibreOffice (incluida) |
| **Navegador de Archivos**         | Sin GUI (usa comandos como `ls`, `cp`) | Nautilus (GNOME), Dolphin (KDE)            | Nemo (Cinnamon)           | Nautilus (GNOME)       |
| **Navegador de Internet**         | Lynx (opcional)                        | Firefox                                    | Firefox o Chromium        | Firefox                |
| **Gestor de Paquetes**            | `apt`                                  | `apt` + Synaptic (opcional)                | `apt` + Gestores gráficos | `dnf` + GNOME Software |
| **Herramientas de Configuración** | Edición manual de archivos             | GNOME Settings u otro, según el escritorio | Cinnamon Settings         | GNOME Settings         |