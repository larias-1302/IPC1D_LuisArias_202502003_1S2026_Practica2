class CustomRenderer extends BarRenderer {
    public int comp1 = -1;
    public int comp2 = -1;
    public int swap1 = -1;
    public int swap2 = -1;
    public boolean[] ordenado;

    public CustomRenderer(int size) {
        ordenado = new boolean[size];
    }
    @Override
    public Paint getItemPaint(int row, int column) {
        if (ordenado[column]) return Color.GREEN;
        if (column == swap1 || column == swap2) return Color.RED;
        if (column == comp1 || column == comp2) return Color.ORANGE;
        return Color.CYAN;
    }
}
