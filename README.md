StickerBoard 

Aplicación Windows Forms en C# que permite crear, visualizar y gestionar stickers (formas geométricas y personalizadas) en un lienzo.
El usuario puede seleccionar el tipo de figura, su posición, tamaño y color, generando los stickers mediante un patrón Factory.

 Descripción del Proyecto

StickerBoard es un programa interactivo que simula un tablero digital donde el usuario puede “pegar” figuras de distintos tipos (rectángulos, círculos, estrellas, nubes) dentro de un PictureBox que actúa como lienzo.

Cada sticker se crea con un color y tamaño definido, y se dibuja automáticamente cuando se presiona el botón CREAR.
También se puede limpiar el lienzo con el botón LIMPIAR.

El programa aplica:

Programación orientada a objetos (POO).

Patrón de diseño Factory Method.

Uso de eventos (Paint, Click, etc.) en Windows Forms.

Validación de entradas y control de rangos.

 Estructura del Proyecto

StickerBoard1

StickerBoard1.cs → Lógica principal del formulario
StickerFactory.cs → Clase Factory que crea los distintos tipos de stickers
Sticker.cs → Clase base abstracta para las figuras
StickerRectangulo.cs → Clase derivada (Rectángulo)
StickerCirculo.cs → Clase derivada (Círculo)
StickerEstrella.cs → Clase derivada (Estrella)
StickerNube.cs → Clase derivada (Nube)
StickerBoard1.Designer.cs → Diseño visual del formulario
Program.cs → Punto de entrada del proyecto
README.txt → Documento explicativo del proyecto

Controles del Formulario

cmbSticker: ComboBox para elegir el tipo de figura (Rectángulo, Círculo, Estrella, Nube).

nudX: Coordenada X de la figura dentro del lienzo.

nudY: Coordenada Y de la figura dentro del lienzo.

nudSize: Tamaño (diámetro/lado) de la figura.

pbColor: Cuadro de color que abre un ColorDialog para elegir color.

btnCrear: Botón que crea y dibuja un nuevo sticker.

btnLimpiar: Borra todos los stickers del lienzo.

txtContador: Muestra el número total de stickers creados.

pblLienzo: PictureBox que actúa como lienzo de dibujo.

 Funcionamiento del Código

Inicialización:
Al iniciar el formulario se cargan los tipos de stickers y se configuran los límites de los controles numéricos.

Selección de Color:
El usuario selecciona un color haciendo clic en el cuadro pbColor, que abre un cuadro de diálogo ColorDialog.

Creación de Sticker:
Al hacer clic en CREAR, se validan los datos y se crea un nuevo objeto mediante StickerFactory, que luego se agrega a la lista y se dibuja en el lienzo.

Dibujo en el Lienzo:
El evento Paint del PictureBox recorre la lista y dibuja cada sticker con su método Dibujar().

Limpieza:
El botón LIMPIAR borra la lista y actualiza el lienzo.

 Patrón de Diseño Usado: Factory Method

El StickerFactory centraliza la creación de las figuras, evitando usar directamente new en el formulario principal.

Ejemplo:

public static class StickerFactory
{
    public enum TipoSticker { Rectangulo, Circulo, Estrella, Nube }

    public static Sticker CrearSticker(TipoSticker tipo, int x, int y, int size, Color color)
    {
        switch (tipo)
        {
            case TipoSticker.Rectangulo: return new StickerRectangulo(x, y, size, color);
            case TipoSticker.Circulo: return new StickerCirculo(x, y, size, color);
            case TipoSticker.Estrella: return new StickerEstrella(x, y, size, color);
            case TipoSticker.Nube: return new StickerNube(x, y, size, color);
            default: throw new ArgumentException("Tipo de sticker no válido");
        }
    }
}

 Ejecución del Programa

Abrir el proyecto en Visual Studio.

Asegurarse de que el formulario principal sea StickerBoard1.

Ejecutar con F5.

Seleccionar tipo de sticker, posición, tamaño y color.

Presionar CREAR para dibujarlo en el lienzo.

Usar LIMPIAR para borrar el contenido.

Requisitos

Lenguaje: C#

Framework: .NET Framework 4.8 o superior

Entorno: Visual Studio 2022 (recomendado)

Tipo de Proyecto: Windows Forms App (.NET Framework)

Autor: Juan David Urrego Jaramillo - Herramientas de Programación 2 - 2025-2 - G-002.

<img width="997" height="542" alt="image" src="https://github.com/user-attachments/assets/d6fa9aee-649e-4cf0-9d31-3fbb509fc676" />

<img width="1005" height="536" alt="image" src="https://github.com/user-attachments/assets/6cde09ae-0128-4f66-9b2d-2e9c629ee458" />

<img width="1001" height="535" alt="image" src="https://github.com/user-attachments/assets/be9170d3-12ae-4a83-b8c7-5807af0e982e" />

<img width="1002" height="532" alt="image" src="https://github.com/user-attachments/assets/e8931d68-a0d4-4137-aa42-499d9d6d03ea" />

<img width="1008" height="541" alt="image" src="https://github.com/user-attachments/assets/c72ccb88-80e5-4088-999b-afa0396dfa3d" />

<img width="998" height="536" alt="image" src="https://github.com/user-attachments/assets/786a18ca-819a-458a-bb54-1005a626782b" />
