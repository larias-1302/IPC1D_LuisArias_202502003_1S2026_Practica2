package practica4_ipc1_lab;
public class Datos {
    private int[] arregloOriginal;
    private int[] arregloTrabajo;
    // Guardar datos
    public void setArreglo(int[] datos) {
        this.arregloOriginal = datos.clone();
        this.arregloTrabajo = datos.clone();
    }

    // Obtener arreglo que se va a ordenar
    public int[] getArreglo() {
        return arregloTrabajo;
    }

    // Obtener arreglo original (para reportes)
    public int[] getOriginal() {
        return arregloOriginal;
    }

    // Reiniciar antes de ordenar
    public void reset() {
        if (arregloOriginal != null) {
            arregloTrabajo = arregloOriginal.clone();
        }
    } 
}
