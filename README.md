# EXAMENU5
package e_uv;

import java.io.BufferedReader;
import java.io.File;
import java.io.FileReader;
import java.io.IOException;

public class E_UV {

    public static void main(String[] args) {

        int[] matriz = LeerTxt();

        System.out.println("MATRIZ LEIDA");
        System.out.println("------");
        for (int filas = 0; filas < matriz.length; filas++) {
            System.out.print(matriz[filas] + ", ");
            System.out.print("");
        }

        quicksort(matriz, 0, matriz.length - 1);

        System.out.println("\n\nMATRIZ ORDENADA");
        System.out.println("------");
        for (int filas = 0; filas < matriz.length; filas++) {
            System.out.print(matriz[filas] + ", ");
            System.out.print("");
        }
    }

    private static int[] LeerTxt() {

        File archivo = null;
        FileReader Fr = null;
        BufferedReader br = null;

        int matriz[] = null;

        try {
            archivo = new File("C:/numeros.txt"); // Ruta desde donde se lee el txt
            Fr = new FileReader(archivo.toString());
            br = new BufferedReader(Fr);
            String linea;
            String delimiter = ","; //Separador dentro del txt.

            while (((linea = br.readLine()) != null)) {

                String a[] = linea.split(delimiter);
                matriz = new int[a.length];

                for (int l = 0; l < a.length; l++) {
                    matriz[l] = Integer.parseInt(a[l]);
                }
            }

        } catch (IOException e) {
            System.out.println(e);
        }
        return matriz;
    }

    private static void quicksort(int arreglo[], int izquierda, int derecha) {
        if (izquierda < derecha) {
            int indiceParticion = particion(arreglo, izquierda, derecha);
            quicksort(arreglo, izquierda, indiceParticion);
            quicksort(arreglo, indiceParticion + 1, derecha);
        }
    }

    private static int particion(int arreglo[], int izquierda, int derecha) {
        int pivote = arreglo[izquierda];

        // Ciclo infinito
        while (true) {
            while (arreglo[izquierda] < pivote) {
                izquierda++;
            }
            while (arreglo[derecha] > pivote) {
                derecha--;
            }
            if (izquierda >= derecha) {
                return derecha;
            } else {
                int temporal = arreglo[izquierda];
                arreglo[izquierda] = arreglo[derecha];
                arreglo[derecha] = temporal;
                izquierda++;
                derecha--;
            }
            // El while se repite hasta que izquierda >= derecha
        }
    }

}
