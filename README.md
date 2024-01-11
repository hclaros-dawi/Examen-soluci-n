# EJERCICIOS BLOQUE 1

En las siguientes líneas de código se ha implementado un programa que consiste en un menú, el cual contiene un conjunto de opciones a las cuales, a través de un switch, accederemos determinadas funciones, que realizan diferentes acciones al recibir determinados parámetros. 
Las funciones que se realizan en el programa son las siguientes: 

- _decimalBinario_: Esta función recibe por parámetro un número entero decimal y lo muestra por pantalla en binario.
- _binarioDecimal_: Esta función recibe por parámetro un número entero binario y lo muestra por pantalla en decimal.
- _esPar_: Esta función recibe por parámetro un número entero y devuelve un booleano true y false si no lo es.
- _primerosNumerosPares_: Esta función recibe por parámetro un número entero n y muestra por pantalla todos los números pares entre 0 y n.
- _menu_: Esta función contiene las opciones que el usuario puede seleccionar.

```
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int opcion;
        do {
            menu();

            opcion = scanner.nextInt();

            switch (opcion) {
                case 1:
                    System.out.println("Has escogido: Decimal a binario. Introduce un número decimal: ");
                    int numero = scanner.nextInt();
                    decimalBinario(numero);
                    break;
                case 2:
                    System.out.println("Has escogido Binario a decimal. Introduce un número binario: ");
                    long numeroBinario = scanner.nextLong();
                    binarioDecimal(numeroBinario);
                    break;
                case 3:
                    System.out.println("Has escogido: Es par?. Introduce un número para verificar si es par (true): ");
                    int numero2 = scanner.nextInt();
                    esPar(numero2);
                    break;
                case 4:
                    System.out.println("Has escogido: Calcula pares de 0 a n. Introduce un número: ");
                    int n = scanner.nextInt();
                    primerosNumerosPares(n);
                    break;
                case 0:
                    System.out.println("Has escogido: Salir");
                    break;
                default:
                    System.out.println("Opción no válida");
            }

        } while (opcion != 0);
    }
    public static void menu() {
        System.out.println("Escoge una de las siguientes opciones: ");
        System.out.println("1. Decimal a binario");
        System.out.println("2. Binario a decimal");
        System.out.println("3. Es par?");
        System.out.println("4. Calcula pares de 0 a n");
        System.out.println("0. Salir");
    }


    public static void decimalBinario(int numero) {
        if (numero < 0) {
            System.out.println("Número no válido, debe ser positivo");
            return;
        }
        int binario = 0;
        while (numero > 0) {
            int residuo = numero % 2;
            binario = binario * 10 + residuo;  //Creamos la variable binaria y agregamos el resultado del residuo donde está 0
            numero = numero / 2;
        }
        int binarioInvert = 0;
        while (binario != 0) {
            int ultima = binario % 10; //Del binario, obtenemos la última cifra
            binarioInvert = binarioInvert * 10 + ultima;  //Creamos la variable del binario invertida y agregamos la última cifra en la posición 0 (la primera)
            binario = binario / 10; //Deja la parte restante del binario que no contiene la cifra reordenada
        }
        System.out.println("El binario es: " + binarioInvert);
    }


    public static void binarioDecimal(long numeroBinario) {
        int n = 0;
        int decimal = 0;
        while (numeroBinario > 0) {
            int cifra = (int) (numeroBinario % 10);
            decimal += (int) (Math.pow(2, n) * cifra);
            numeroBinario = numeroBinario / 10;
            n++;
        }
        System.out.println("El número decimal es: " + decimal);
    }


    public static void primerosNumerosPares(int n) {
        if (n > 0) {
            for (int i = 0; i < n; i++) {
                if (i % 2 == 0) {
                    System.out.println(i);
                }
            }

        } else {
            System.out.println("Introduce un número positivo");
        }
    }

    public static void esPar(int numero2) {
        boolean numPar = (numero2 % 2 == 0);
        System.out.println(numPar);
    }
}
```

-----------------------------------------
# EJERCICIOS BLOQUE 2

Una empresa suele transportar líquidos o materias primas como tierra, grava arena o similares, es decir, mide el transporte según el volúmen del material a transportar.
En las siguientes líneas de código se ha implementado un programa que consiste en determinar cuantos viajes le hace falta hacer para completar cada encargo.

Las funciones que se implementan son:

-_volumenCilindro_: V = Pi * radio ^ 2 * longitud

-_volumenPrismaRectangular_: V = arista1 * arista2 * arista3

```
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
```


