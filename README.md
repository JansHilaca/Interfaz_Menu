# Ejecuccion:

![imagen](https://github.com/JansHilaca/Interfaz_Menu/assets/168945853/0d5a44e4-019b-4cf7-a61d-f5ade9a7f748)

![imagen](https://github.com/JansHilaca/Interfaz_Menu/assets/168945853/313ad621-e809-4d79-bb12-406f7fe450de)

![imagen](https://github.com/JansHilaca/Interfaz_Menu/assets/168945853/f335257d-2e3c-47b8-838e-ab56516fccd0)

![imagen](https://github.com/JansHilaca/Interfaz_Menu/assets/168945853/f357a538-400a-479e-b418-a89bc5becafc)


# Interfaz Gráfica de Usuario en JavaFX

Este proyecto implementa una aplicación básica de JavaFX con una interfaz gráfica de usuario (GUI) que incluye una barra de menú.

## Descripción

La aplicación presenta una ventana con una barra de menú en la parte superior, que contiene los menús "Archivo", "Editar" y "Ayuda". Cada menú incluye varios elementos de menú, algunos de los cuales realizan acciones específicas, como cerrar la aplicación o mostrar información en la consola.

## Estructura del Código

### Paquete y Clase Principal

- **Paquete y Declaración de Clase**: La clase `GUIJavaFX` pertenece al paquete `Main` y extiende `Application`, lo que la convierte en una aplicación JavaFX.

### Método `start`

- **Sobrescribe el Método `start`**: Sobrescribe el método `start` para configurar la interfaz de usuario. Este método es el punto de entrada principal de la aplicación JavaFX y recibe un objeto `Stage`, que representa la ventana principal.

### Layout Principal

- **Uso de BorderPane**: Utiliza un `BorderPane` como layout principal. El `BorderPane` permite organizar la interfaz en cinco regiones: superior, inferior, izquierda, derecha y centro.

### Barra de Menú

- **Creación de MenuBar**: Crea una barra de menú (`MenuBar`).
- **Menús Principales**: Añade tres menús principales: "Archivo", "Editar" y "Ayuda".
- **Elementos de Menú**: Añade elementos de menú a cada menú principal. Por ejemplo, el menú "Archivo" incluye elementos como "Nuevo", "Abrir", "Guardar" y "Salir". Además, se utilizan separadores (`SeparatorMenuItem`) para organizar los elementos de manera lógica.

### Acciones de los Menús

- **Definición de Acciones**: Define acciones para ciertos elementos de menú. Por ejemplo:
  - **Salir**: Al seleccionar "Salir", la aplicación se cierra mediante `System.exit(0)`.
  - **Acerca de**: Al seleccionar "Acerca de", se muestra un mensaje en la consola indicando "Información de la aplicación".

### Configuración de la Ventana

- **Creación de la Escena**: Crea una escena (`Scene`) con el `BorderPane` como raíz y especifica un tamaño de 400x300 píxeles.
- **Establecimiento de la Escena en el Escenario Principal**: Establece la escena en el escenario principal (`primaryStage`).
- **Título de la Ventana**: Fija el título de la ventana como "Interfaz Gráfica de Usuario en JavaFX".
- **Mostrar la Ventana**: Llama al método `show()` del `primaryStage` para mostrar la ventana.

### Método Principal

- **Lanzamiento de la Aplicación**: El método `main` lanza la aplicación llamando a `launch(args)`. Este método es el punto de entrada estándar de cualquier aplicación JavaFX.

## Código

```java
package Main;

import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.BorderPane;
import javafx.stage.Stage;

public class GUIJavaFX extends Application {

    @Override
    public void start(Stage primaryStage) {
        // Creación del layout principal
        BorderPane root = new BorderPane();

        // Creación de la barra de menú
        MenuBar menuBar = new MenuBar();

        // Menús principales
        Menu fileMenu = new Menu("Archivo");
        Menu editMenu = new Menu("Editar");
        Menu helpMenu = new Menu("Ayuda");

        // Elementos del menú "Archivo"
        MenuItem newItem = new MenuItem("Nuevo");
        MenuItem openItem = new MenuItem("Abrir");
        MenuItem saveItem = new MenuItem("Guardar");
        MenuItem exitItem = new MenuItem("Salir");

        // Elementos del menú "Editar"
        MenuItem cutItem = new MenuItem("Cortar");
        MenuItem copyItem = new MenuItem("Copiar");
        MenuItem pasteItem = new MenuItem("Pegar");

        // Elemento del menú "Ayuda"
        MenuItem aboutItem = new MenuItem("Acerca de");

        // Añadir elementos a los menús principales
        fileMenu.getItems().addAll(newItem, openItem, saveItem, new SeparatorMenuItem(), exitItem);
        editMenu.getItems().addAll(cutItem, copyItem, pasteItem);
        helpMenu.getItems().addAll(aboutItem);

        // Añadir menús a la barra de menú
        menuBar.getMenus().addAll(fileMenu, editMenu, helpMenu);

        // Definir acciones para los elementos del menú
        exitItem.setOnAction(e -> System.exit(0));
        aboutItem.setOnAction(e -> System.out.println("Información de la aplicación"));

        // Configurar el layout principal
        root.setTop(menuBar);

        // Crear y configurar la escena
        Scene scene = new Scene(root, 400, 300);
        primaryStage.setScene(scene);
        primaryStage.setTitle("Interfaz Gráfica de Usuario en JavaFX");
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
