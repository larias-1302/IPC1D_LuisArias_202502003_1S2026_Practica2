public void actualizarGrafica(int[] arr) {
    dataset.clear();

    for (int i = 0; i < arr.length; i++) {
        dataset.addValue(arr[i], "Valores", String.valueOf(i));
    }
}
