import java.util.Scanner;

public class bloque2 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("¿Transporte de sólido (1) o líquido (2)?");
        int opcion = scanner.nextInt();
        double volumen = 0;

        if (opcion == 1){
            System.out.println("¿Cuánto mide el radio de la cisterna?");
            double radio = scanner.nextDouble();
            System.out.println("¿Cuánto mide el largo de la cisterna?");
            double longitud = scanner.nextDouble();

            volumen= volumenCilindro(radio, longitud);
        } else if (opcion == 2){
            System.out.println("¿Cuánto mide la arista 1 del camión?");
            double arista1 = scanner.nextDouble();
            System.out.println("¿Cuánto mide la arista 2 del camión?");
            double arista2 = scanner.nextDouble();
            System.out.println("¿Cuánto mide la arista 3 del camión?");
            double arista3 = scanner.nextDouble();

            volumen= volumenPrismaRectangular(arista1, arista2, arista3);
        } else {
            System.out.println("No es una opción válida");
            System.out.println("¿Transporte de sólido (1) o líquido (2)?");
            opcion = scanner.nextInt();
        }
        System.out.println("¿Cuántos centímetros cúbicos tenemos que transportar");
        double cm3 = scanner.nextDouble();

        System.out.println("El camión tiene " + volumen + " centímetros cúbicos");
        double capacidad = volumen / 1000000;
        System.out.println("Caben " + capacidad + " metros cúbicos");
        int numViajes = (int) (cm3/capacidad);
        System.out.println("Tienes que hacer " + numViajes + " viajes");


    }

    public static double volumenCilindro(double radio, double longitud){
        return (Math.PI) * Math.pow(radio, 2) * longitud;
    }
    public static double volumenPrismaRectangular(double arista1, double arista2, double arista3){
        return arista1 * arista2 * arista3;
    }
}
