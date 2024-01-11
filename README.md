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
