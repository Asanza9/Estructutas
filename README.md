# Estructutas
import java.io.File;
import java.io.FileWriter;
import java.io.FileReader;
import java.io.BufferedReader;
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        // Ruta de la carpeta donde se creará el archivo
        String carpeta = "/ruta/de/la/carpeta";
        
        // Nombre del archivo a crear
        String nombreArchivo = "archivo.txt";
        
        // Contenido a escribir en el archivo
        String contenido = "¡Hola, mundo desde Java!";
        
        // Crear el archivo en la carpeta especificada
        crearArchivo(carpeta, nombreArchivo, contenido);
        
        // Leer el archivo
        leerArchivo(carpeta, nombreArchivo);
    }
    
    public static void crearArchivo(String carpeta, String nombreArchivo, String contenido) {
        try {
            File directorio = new File(carpeta);
            if (!directorio.exists()) {
                directorio.mkdirs();
            }
            
            File archivo = new File(directorio, nombreArchivo);
            FileWriter escritor = new FileWriter(archivo);
            escritor.write(contenido);
            escritor.close();
            
            System.out.println("Archivo creado exitosamente en: " + archivo.getAbsolutePath());
        } catch (IOException e) {
            System.out.println("Error al crear el archivo: " + e.getMessage());
        }
    }
    
    public static void leerArchivo(String carpeta, String nombreArchivo) {
        try {
            File archivo = new File(carpeta, nombreArchivo);
            FileReader lector = new FileReader(archivo);
            BufferedReader buffer = new BufferedReader(lector);
            String linea;
            System.out.println("Contenido del archivo:");
            while ((linea = buffer.readLine()) != null) {
                System.out.println(linea);
            }
            buffer.close();
        } catch (IOException e) {
            System.out.println("Error al leer el archivo: " + e.getMessage());
        }
    }
}
