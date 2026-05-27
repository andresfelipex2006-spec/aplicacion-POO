# aplicacion-POO
import java.util.ArrayList;
import java.util.Scanner;

// ================== CLASE PERSONA ==================
class Persona {
    String nombre;
    String apellido;
    String genero;
    int edad;

    // Constructor
    public Persona(String nombre, String apellido, String genero, int edad) {
        this.nombre = nombre;
        this.apellido = apellido;
        this.genero = genero;
        this.edad = edad;
    }

    // Método para clasificar usando operador ternario
    public String clasificacion() {
        return (edad < 12) ? "Infante" :
               (edad < 18) ? "Adolescente" :
               (edad >= 60) ? "Adulto Mayor" : "Adulto";
    }

    // Mostrar datos
    public void mostrar() {
        System.out.println(nombre + " " + apellido + " | " + genero + " | Edad: " + edad + " | Tipo: " + clasificacion());
    }
}

// ================== CLASE PRINCIPAL ==================
public class AppPersonas {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        ArrayList<Persona> lista = new ArrayList<>();

        int infantes = 0;
        int adolescentes = 0;
        int adultosMayores = 0;

        String continuar;

        do {
            sc.nextLine();

            // ================== INGRESO DE DATOS ==================
            System.out.print("Nombre: ");
            String nombre = sc.nextLine();

            System.out.print("Apellido: ");
            String apellido = sc.nextLine();

            System.out.print("Género: ");
            String genero = sc.nextLine();

            System.out.print("Edad: ");
            int edad = sc.nextInt();

            // Crear objeto
            Persona p = new Persona(nombre, apellido, genero, edad);
            lista.add(p);

            // ================== CONTADORES ==================
            String tipo = p.clasificacion();

            infantes += (tipo.equals("Infante")) ? 1 : 0;
            adolescentes += (tipo.equals("Adolescente")) ? 1 : 0;
            adultosMayores += (tipo.equals("Adulto Mayor")) ? 1 : 0;

            // ================== CONTINUAR ==================
            sc.nextLine();
            System.out.print("¿Desea continuar? (si/no): ");
            continuar = sc.nextLine();

        } while (continuar.equalsIgnoreCase("si"));

        // ================== RESULTADOS ==================
        System.out.println("\n=== PERSONAS REGISTRADAS ===");
        for (Persona p : lista) {
            p.mostrar();
        }

        System.out.println("\n=== CONTADORES ===");
        System.out.println("Infantes: " + infantes);
        System.out.println("Adolescentes: " + adolescentes);
        System.out.println("Adultos Mayores: " + adultosMayores);
    }
}
