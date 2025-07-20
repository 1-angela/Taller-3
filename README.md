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
