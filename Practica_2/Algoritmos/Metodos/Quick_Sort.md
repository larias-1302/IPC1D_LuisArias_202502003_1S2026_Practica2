public void quickSort(int[] arr, int low, int high, boolean asc, int velocidad) throws InterruptedException {
    if (low >= high) return;

    iteraciones++;
    actualizarEstadisticas();
    int pi = partition(arr, low, high, asc, velocidad);

    quickSort(arr, low, pi - 1, asc, velocidad);
    quickSort(arr, pi + 1, high, asc, velocidad);
}
