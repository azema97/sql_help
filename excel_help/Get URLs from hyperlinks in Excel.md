# Extraiga direcciones reales de hipervínculos con la función de definición de usuario

La siguiente función definida por el usuario también puede extraer la URL real de los hipervínculos.

1. Mantenga pulsado el ALT + F11 teclas para abrir el **Microsoft Visual Basic** para aplicaciones ventana.
2. Haga click derecho en la spreadsheet, seleccione "Insertar" > "Módulo" y pegue el siguiente código en el Ventana de módulo.

```vba
Function GetURL(pWorkRng As Range) As String
'Updateby Extendoffice
    GetURL = pWorkRng.Hyperlinks(1).Address
End Function
```

3. Guarde el código y cierre la ventana, seleccione una celda en blanco para escribir esta fórmula `=ObtenerURL (A2)` (A2 es la celda en la que se encuentra el hipervínculo) y presione Enviar botón. Puede ver que se extrae la dirección real del hipervínculo.


