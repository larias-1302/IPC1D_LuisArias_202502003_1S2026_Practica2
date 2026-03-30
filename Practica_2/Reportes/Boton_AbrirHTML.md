try {
    File file = new File("reporte_" + historial.size() + ".html");
    Desktop.getDesktop().browse(file.toURI());
}catch (Exception e) {
    e.printStackTrace();
}
