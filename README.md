# Estructutas
import java.io.File;
import java.io.FileWriter;
import java.io.FileReader;
import java.io.BufferedReader;
import java.io.IOException;

public class Archivo {

    public static void main(String[] args) {
        // Nombre del archivo
        String nombreArchivo = "archivo.txt";

        // Contenido a escribir en el archivo
        String contenido = "Hola, este es un archivo de ejemplo.";

        // Escribir en el archivo
        escribirArchivo(nombreArchivo, contenido);

        // Leer el archivo
        String contenidoLeido = leerArchivo(nombreArchivo);
        System.out.println("Contenido del archivo:");
        System.out.println(contenidoLeido);
    }

    // Método para escribir en el archivo
    public static void escribirArchivo(String nombreArchivo, String contenido) {
        try {
            FileWriter escritor = new FileWriter(nombreArchivo);
            escritor.write(contenido);
            escritor.close();
            System.out.println("Se ha escrito en el archivo correctamente.");
        } catch (IOException e) {
            System.out.println("Ocurrió un error al escribir en el archivo: " + e.getMessage());
        }
    }

    // Método para leer el archivo
    public static String leerArchivo(String nombreArchivo) {
        StringBuilder contenido = new StringBuilder();
        try {
            FileReader lector = new FileReader(nombreArchivo);
            BufferedReader buffer = new BufferedReader(lector);
            String linea;
            while ((linea = buffer.readLine()) != null) {
                contenido.append(linea).append("\n");
            }
            buffer.close();
        } catch (IOException e) {
            System.out.println("Ocurrió un error al leer el archivo: " + e.getMessage());
        }
        return contenido.toString();
    }
}
