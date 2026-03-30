public void cargarTabla(ArrayList<Ejecucion> historial) {
    DefaultTableModel modelo = (DefaultTableModel) tblHistorial.getModel();
    modelo.setRowCount(0);

    for (Ejecucion e : historial) {
        modelo.addRow(new Object[]{e.numero,e.algoritmo,e.orden,e.n,e.comparaciones,e.intercambios,e.iteraciones,e.tiempo});
    }
}
