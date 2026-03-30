public void shellSort(int[] arr, boolean asc, int velocidad) throws InterruptedException {
    int n = arr.length;

    for (int gap = n / 2; gap > 0; gap /= 2) {
        for (int i = gap; i < n; i++) {
            int temp = arr[i];
            int j = i;

            //Comparacion
            renderer.comp1 = i;
            renderer.comp2 = i - gap;

            comparaciones++;
            actualizarEstadisticas();

            paso++;
            agregarLog("[Paso " + paso + "] Comparando arr[" + j + "]=" + arr[j] + " con arr[" + (j - gap) + "]=" + arr[j - gap]);

            int[] copia1 = arr.clone();
            SwingUtilities.invokeLater(() -> actualizarGrafica(copia1));
            Thread.sleep(velocidad);

            while (j >= gap && (asc ? arr[j - gap] > temp : arr[j - gap] < temp)) {
                renderer.comp1 = j;
                renderer.comp2 = j - gap;

                comparaciones++;
                actualizarEstadisticas();

                renderer.swap1 = j;
                renderer.swap2 = j - gap;

                intercambios++;
                actualizarEstadisticas();

                paso++;
                agregarLog("[Paso " + paso + "] Movimiento arr[" + j + "]=" + arr[j] + " ← arr[" + (j - gap) + "]=" + arr[j - gap]);
                arr[j] = arr[j - gap];
                j -= gap;

                int[] copia = arr.clone();
                SwingUtilities.invokeLater(() -> actualizarGrafica(copia));
                Thread.sleep(velocidad);

                renderer.swap1 = -1;
                renderer.swap2 = -1;
            }

            //Lo inserta
            arr[j] = temp;

            int[] copia2 = arr.clone();
            SwingUtilities.invokeLater(() -> actualizarGrafica(copia2));
            Thread.sleep(velocidad);

            iteraciones++;
            actualizarEstadisticas();
        }
    }

    //Lo marca de verde
    for (int i = 0; i < arr.length; i++) {
        renderer.ordenado[i] = true;
    }

    renderer.comp1 = -1;
    renderer.comp2 = -1;
}
