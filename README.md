# Ejecuccion:

![imagen](https://github.com/JansHilaca/Interfaz_Menu/assets/168945853/0d5a44e4-019b-4cf7-a61d-f5ade9a7f748)

![imagen](https://github.com/JansHilaca/Interfaz_Menu/assets/168945853/313ad621-e809-4d79-bb12-406f7fe450de)

![imagen](https://github.com/JansHilaca/Interfaz_Menu/assets/168945853/f335257d-2e3c-47b8-838e-ab56516fccd0)

![imagen](https://github.com/JansHilaca/Interfaz_Menu/assets/168945853/f357a538-400a-479e-b418-a89bc5becafc)


# Interfaz Gráfica de Usuario en JavaFX

Este proyecto implementa una aplicación básica de JavaFX con una interfaz gráfica de usuario (GUI) que incluye una barra de menú.

## Funcionalidades:

- **Nuevo:** Al seleccionar esta opción, se abre un diálogo que permite al usuario crear un nuevo archivo. Una vez que el usuario ingresa el nombre del nuevo archivo y lo confirma, el nombre se muestra en la consola como feedback para la acción realizada.

- **Abrir:** Esta opción abre un cuadro de diálogo que permite al usuario seleccionar un archivo existente. Una vez que el usuario selecciona un archivo y lo confirma, el nombre del archivo seleccionado se muestra en la consola para indicar que la acción ha sido realizada.

- **Guardar:** Al seleccionar esta opción, se abre un diálogo para guardar un archivo. Se escribe un contenido de ejemplo en el archivo, y una vez que el usuario guarda el archivo y lo confirma, se muestra el nombre del archivo en la consola como confirmación de la acción completada.

- **Salir:** Cuando se selecciona esta opción, se muestra un cuadro de confirmación pidiendo al usuario que confirme si realmente desea cerrar la aplicación. Si el usuario confirma, la aplicación se cierra. Este enfoque proporciona una experiencia más amigable al usuario al evitar cierres accidentales.

- **Cortar, Copiar y Pegar:** Aunque estos elementos de menú se incluyen en la barra de menú, actualmente no tienen ninguna acción asociada en el código proporcionado. Podrían implementarse en futuras iteraciones de desarrollo para mejorar la funcionalidad de la aplicación.

- **Acerca de:** Esta opción muestra información sobre la aplicación en un cuadro de diálogo. Al seleccionarla, se muestra un mensaje en la consola que proporciona detalles sobre la aplicación, como su nombre, versión o información de contacto. Esto puede ayudar a los usuarios a comprender mejor el propósito y la función de la aplicación.


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
