# Taller-3
Calculadora Nutricional

import java.util.Scanner;

public class CalculadoraNutricional {

    public static void main(String[] args) {

        // DATOS //
        double totalGrasas = 0;
        double totalCalorias = 0;
        double totalProteinas = 0;
        double totalCarbohidratos = 0;
        double totalVegetales =0;
        
        Scanner scanner = new Scanner(System.in);

        System.out.print("Ingrese la cantidad de ingredientes: ");
        int cantidadIngredientes = scanner.nextInt();

        for (int i = 1; i <= cantidadIngredientes; i++) {
            System.out.println("\nIngrediente " + i);

            System.out.print("Ingrese el tipo de nutriente (proteina, grasa, carbohidrato, Vegetales): ");
            String tipo = scanner.next().toLowerCase();

            System.out.print("Ingrese la cantidad en gramos consumidos: ");
            double gramos = scanner.nextDouble();

            // CÁLCULO DE NUTRIENTES //
            switch (tipo) {
                
                case "proteina":
                    totalProteinas += gramos;
                    totalCalorias += gramos * 4;
                    break;
                case "grasa":
                    totalGrasas += gramos;
                    totalCalorias += gramos * 9;
                    break;
                case "carbohidrato":
                    totalCarbohidratos += gramos;
                    totalCalorias += gramos * 4;
                case "vegetales":
                    totalVegetales += gramos;
                    totalCalorias += gramos *4;
                    break;
                default:
                    System.out.println("Tipo no válido. Intente nuevamente.");
                    i--; // Repetir el ciclo
                    break;
            }
        }

        // RESULTADO DE CALORÍAS CONSUMIDAS //
        System.out.println("\n--- Resumen Nutricional ---");
        System.out.println("Calorías: " + (int) totalCalorias + " kcal");
        System.out.println("Proteínas: " + (int) totalProteinas + " g");
        System.out.println("Grasas: " + (int) totalGrasas + " g");
        System.out.println("Carbohidratos: " + (int) totalCarbohidratos + " g");
        System.out.println("Vegetales: " + (int) totalVegetales + "g");

        // Evaluación nutricional simple
        if (totalCalorias <= 2000) {
            System.out.println("Valor nutricional: ACEPTABLE");
        } else {
            System.out.println("Valor nutricional: NO ACEPTABLE (Exceso de calorías)");
        }

        scanner.close();
    }
}








Lista de películas por año de lanzamiento:

import java.util.Scanner;

public class OrdenarPeliculas {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("¿Cuántas películas desea ingresar?: ");
        int n = scanner.nextInt();
        scanner.nextLine(); // Limpiar buffer

        // Matriz: cada fila es una película (título, año y género)
        String[][] peliculas = new String[n][3];

        // Para datos ingrasados
        for (int i = 0; i < n; i++) {
            System.out.println("\n Película #" + (i + 1));
            System.out.print("Título: ");
            peliculas[i][0] = scanner.nextLine();

            System.out.print("Año de lanzamiento: ");
            peliculas[i][1] = scanner.nextLine();

            System.out.print("Género: ");
            peliculas[i][2] = scanner.nextLine();
        }

        // Ordenar por año 
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - 1 - i; j++) {
                int anio1 = Integer.parseInt(peliculas[j][1]);
                int anio2 = Integer.parseInt(peliculas[j + 1][1]);
                if (anio1 > anio2) {
                    // Intercambiar filas completas
                    String[] temp = peliculas[j];
                    peliculas[j] = peliculas[j + 1];
                    peliculas[j + 1] = temp;
                }
            }
        }

        // Mostrar películas ordenadas
        System.out.println("\n Películas ordenadas por año de lanzamiento:");
        for (int i = 0; i < n; i++) {
            System.out.println(peliculas[i][1] + " - " + peliculas[i][0] + " (" + peliculas[i][2] + ")");
        }

        scanner.close();
    }
}
