package practica4_ipc1_lab;
import java.util.ArrayList;
import javax.swing.JOptionPane;

public class Menu extends javax.swing.JFrame {
    private static final java.util.logging.Logger logger = java.util.logging.Logger.getLogger(Menu.class.getName());
    ArrayList<Ejecucion> historial;
    
    public Menu(ArrayList<Ejecucion> historial) {
        initComponents();
        this.setLocationRelativeTo(null);
        this.historial = historial;
    }
