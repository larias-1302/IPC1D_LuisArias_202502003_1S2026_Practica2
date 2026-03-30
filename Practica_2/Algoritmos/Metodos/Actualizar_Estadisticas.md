public void actualizarEstadisticas() {
    SwingUtilities.invokeLater(() -> {
        lblComparaciones.setText("Comparaciones: " + comparaciones);
        lblIntercambios.setText("Intercambios: " + intercambios);
        lblIteraciones.setText("Iteraciones: " + iteraciones);
    });
}
