package practica4_ipc1_lab;
import java.awt.Desktop;
import java.io.File;
import java.util.ArrayList;
import javax.swing.table.DefaultTableModel;

public class Reportes extends javax.swing.JFrame { 
    private static final java.util.logging.Logger logger = java.util.logging.Logger.getLogger(Reportes.class.getName());
    ArrayList<Ejecucion> historial;
    
    public Reportes(ArrayList<Ejecucion> historial) {
        initComponents();
        this.setLocationRelativeTo(null);
        this.historial = historial;
        cargarTabla(historial);
    }
    
    public Reportes() {
        initComponents();
    }
