# Proyectos
En este repositorio se encuentran los archivos de código y otros necesarios para poder ejecutar y reproducir distintos proyectos que he hecho.

## Web Scrapping
En la carpeta `WebScrapping` se encuentran los archivos necesario y resultantes del proyecto de recopilar información de [La Jornada](https://www.jornada.com.mx/) sobre asesinatos y masacres del 2013 al 2015.

Es necesario tener instalado google chrome, o cambiar el `chromedriver.exe` por otro driver de un navegador que sí esté instalado, tambien se debe cambiar en la primer celda de código.
El procedimiento, objetivos y demás información está explicada en celdas de Markdown en el archivo `LaJornada.ipynb`

## Crypto y SP500
En la carpeta `EconometriaCrypto` se encuentra el archivo  de Quarto con extensión `.qmd` y el archivo de extensión `.pdf` generado, fue realizado en la aplicación gratuita **RStudio**.

Objetivos, procedimiento y Conclusiones se encuentran descritos en el archivo.

## Simulación de Opciones Financieras
En la carpeta `SimulacionOpciones` se encuentra el notebook de python, realizado en *jupyter* en el cual se simulan los rendimientos y el valor de opciones financieras mediante montecarlo, suponiendo que los precios siguen un **Movimiento Browniano**. Se compara una opción tipo Europea con una tipo Asiática de Strike Variable con ambas la media aritmética y la Geométrica. Se calcula el Coeficiente de correlación entre ambas.
