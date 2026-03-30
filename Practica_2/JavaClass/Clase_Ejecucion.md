package practica4_ipc1_lab;
public class Ejecucion {
    int numero;
    String algoritmo;
    String orden;
    int n;
    int comparaciones;
    int intercambios;
    int iteraciones;
    long tiempo;

    public Ejecucion(int numero, String algoritmo, String orden, int n,
                     int comparaciones, int intercambios, int iteraciones, long tiempo) {
        this.numero = numero;
        this.algoritmo = algoritmo;
        this.orden = orden;
        this.n = n;
        this.comparaciones = comparaciones;
        this.intercambios = intercambios;
        this.iteraciones = iteraciones;
        this.tiempo = tiempo;
    }
}
