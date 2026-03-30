public void generarReporteHTML(int[] original, int[] ordenado, String algoritmo, String orden, int comparaciones, int intercambios, int iteraciones, long tiempo, String velocidad) {
    try {
        FileWriter writer = new FileWriter("reporte_" + contadorEjecuciones + ".html");

        writer.write("<html><head><title>Reporte</title></head><body>");
        writer.write("<h1>Resumen de Ejecución</h1>");

        writer.write("<p><b>Algoritmo:</b> " + algoritmo + "</p>");
        writer.write("<p><b>Orden:</b> " + orden + "</p>");
        writer.write("<p><b>Velocidad:</b> " + velocidad + "</p>");

        writer.write("<p><b>Arreglo original:</b> " + Arrays.toString(original) + "</p>");
        writer.write("<p><b>Arreglo ordenado:</b> " + Arrays.toString(ordenado) + "</p>");

        writer.write("<p><b>Comparaciones:</b> " + comparaciones + "</p>");
        writer.write("<p><b>Intercambios:</b> " + intercambios + "</p>");
        writer.write("<p><b>Iteraciones:</b> " + iteraciones + "</p>");
        writer.write("<p><b>Tiempo:</b> " + tiempo + " ms</p>");

        writer.write("</body></html>");

        writer.close();

    } catch (Exception e) {
        e.printStackTrace();
    }
}
