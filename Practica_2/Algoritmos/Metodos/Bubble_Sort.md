public void bubbleSort(int[] arr, boolean asc, int velocidad) throws InterruptedException {
    int n = arr.length;

    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            renderer.comp1 = j;
            renderer.comp2 = j + 1;
            
            comparaciones++;
            actualizarEstadisticas();
            
            paso++;
            agregarLog("[Paso " + paso + "] Comparando arr[" + j + "]=" + arr[j] + " con arr[" + (j + 1) + "]=" + arr[j + 1]);

            boolean condicion = asc 
                ? arr[j] > arr[j + 1]
                : arr[j] < arr[j + 1];

            if(condicion){
                renderer.swap1 = j;
                renderer.swap2 = j + 1;

                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;

                intercambios++;
                actualizarEstadisticas();
                paso++;
                agregarLog("[Paso " + paso + "] Intercambio arr[" + j + "]=" + arr[j] + " con arr[" + (j + 1) + "]=" + arr[j + 1]);

                int[] copia = arr.clone();
                SwingUtilities.invokeLater(() -> actualizarGrafica(copia));
                Thread.sleep(velocidad);

                renderer.swap1 = -1;
                renderer.swap2 = -1;
            }

            int[] copia = arr.clone();
            SwingUtilities.invokeLater(() -> actualizarGrafica(copia));
            Thread.sleep(velocidad);
        }
        renderer.ordenado[n - i - 1] = true;
        iteraciones++;
        actualizarEstadisticas();
    }
    renderer.comp1 = -1;
    renderer.comp2 = -1;

    for (int i = 0; i < arr.length; i++) {
        renderer.ordenado[i] = true;
    }

    int[] copia = arr.clone();
    SwingUtilities.invokeLater(() -> actualizarGrafica(copia));
}
