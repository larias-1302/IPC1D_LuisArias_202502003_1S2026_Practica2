public int partition(int[] arr, int low, int high, boolean asc, int velocidad) throws InterruptedException {
    int pivot = arr[high];
    int i = low - 1;

    for (int j = low; j < high; j++) {
        comparaciones++;
        actualizarEstadisticas();
        paso++;
        agregarLog("[Paso " + paso + "] Comparando arr[" + j + "]=" + arr[j] + " con pivote=" + pivot);
        //Compara
        renderer.comp1 = j;
        renderer.comp2 = high;
        boolean condicion = asc ? arr[j] <= pivot : arr[j] >= pivot;

        if (condicion) {
            i++;
            //Intercambia
            intercambios++;
            actualizarEstadisticas();
            paso++;
            agregarLog("[Paso " + paso + "] Intercambio arr[" + i + "]=" + arr[i] + " con arr[" + j + "]=" + arr[j]);
            renderer.swap1 = i;
            renderer.swap2 = j;

            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
            
        }

        int[] copia = arr.clone();
        SwingUtilities.invokeLater(() -> actualizarGrafica(copia));
        Thread.sleep(velocidad);

        //Limpia el SWAP
        renderer.swap1 = -1;
        renderer.swap2 = -1;
    }

    //SWAP final del pivote
    renderer.swap1 = i + 1;
    renderer.swap2 = high;

    int temp = arr[i + 1];
    arr[i + 1] = arr[high];
    arr[high] = temp;
    
    intercambios++;
    actualizarEstadisticas();
    paso++;
    agregarLog("[Paso " + paso + "] Pivote colocado en posición " + (i + 1));

    int[] copia = arr.clone();
    SwingUtilities.invokeLater(() -> actualizarGrafica(copia));
    Thread.sleep(velocidad);

    renderer.swap1 = -1;
    renderer.swap2 = -1;
    return i + 1;
}
