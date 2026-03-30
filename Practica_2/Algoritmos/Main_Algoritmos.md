package practica4_ipc1_lab;
import javax.swing.JOptionPane;
import org.jfree.chart.ChartFactory;
import org.jfree.chart.ChartPanel;
import org.jfree.chart.JFreeChart;
import org.jfree.data.category.DefaultCategoryDataset;
import java.awt.BorderLayout;
import javax.swing.SwingUtilities;
import org.jfree.chart.renderer.category.BarRenderer;
import java.awt.Color;
import java.awt.Paint;
import java.io.BufferedReader;
import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;
import java.util.ArrayList;
import java.util.Arrays;
import javax.swing.JFileChooser;

public class Algortimos extends javax.swing.JFrame {
    private static final java.util.logging.Logger logger = java.util.logging.Logger.getLogger(Algortimos.class.getName());
    Datos datosModelo= new Datos();
    DefaultCategoryDataset dataset;
    JFreeChart chart;
    ChartPanel chartPanel;
    CustomRenderer renderer;
    int comparaciones = 0;
    int intercambios = 0;
    int iteraciones = 0;
    int paso = 0;
    public static ArrayList<Ejecucion> historial = new ArrayList<>();
    public static int contadorEjecuciones = 0;
    
    public Algortimos() {
        initComponents();
        this.setLocationRelativeTo(null);
        
        dataset = new DefaultCategoryDataset();
        chart = ChartFactory.createBarChart("Visualización", "Índice", "Valor", dataset);
        chartPanel = new ChartPanel(chart);
        chartPanel.setPreferredSize(jPanelVisualizacion.getSize());
        
        jPanelVisualizacion.setLayout(new BorderLayout());
        jPanelVisualizacion.add(chartPanel, BorderLayout.CENTER);
        
        jPanelVisualizacion.revalidate();
        jPanelVisualizacion.repaint();

        jPanelVisualizacion.setLayout(new BorderLayout());
        jPanelVisualizacion.add(chartPanel, BorderLayout.CENTER);
        
        renderer = new CustomRenderer(50); // 50 por seguridad
        chart.getCategoryPlot().setRenderer(renderer);
        
        txtLog.setEditable(false);
     
    }
