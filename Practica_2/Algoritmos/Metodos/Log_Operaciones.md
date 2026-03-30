public void agregarLog(String mensaje) {
    SwingUtilities.invokeLater(() -> {
        txtLog.append(mensaje + "\n");
        txtLog.setCaretPosition(txtLog.getDocument().getLength()); // auto scroll
    });
}
