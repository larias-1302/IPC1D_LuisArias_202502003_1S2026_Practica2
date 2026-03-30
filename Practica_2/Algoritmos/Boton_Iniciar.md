new Thread(() -> {
        SwingUtilities.invokeLater(() -> jbtnIniciar.setEnabled(false));

        try{
            int[] arr = datosModelo.getArreglo();
            
            if (arr == null || arr.length == 0) {
                SwingUtilities.invokeLater(() -> JOptionPane.showMessageDialog(this, "No hay datos cargados"));
                SwingUtilities.invokeLater(() -> jbtnIniciar.setEnabled(true));
                return;
            }
            
            int[] copiaOriginal = arr.clone();
            String algoritmo = jcbAlgoritmo.getSelectedItem().toString();
            boolean ascendente = jcbOrden.getSelectedItem().toString().equals("Ascendente");
            int velocidad = 100;
            String vel = jcbVelocidad.getSelectedItem().toString();

            if (vel.equals("Lento")) velocidad = 500;
            else if (vel.equals("Medio")) velocidad = 100;
            else if (vel.equals("Rapido")) velocidad = 20;

            //Renderer
            renderer = new CustomRenderer(50);
            chart.getCategoryPlot().setRenderer(renderer);

            //Reinicio las estadisticas
            comparaciones = 0;
            intercambios = 0;
            iteraciones = 0;
            actualizarEstadisticas();
            paso = 0;
            txtLog.setText("");

            StringBuilder sb = new StringBuilder();

            for (int i = 0; i < arr.length; i++){
                sb.append(arr[i]);
                if (i < arr.length - 1) sb.append(",");
            }

            agregarLog("[Inicio] Arreglo cargado: " + sb.toString());
            long inicio = System.currentTimeMillis();

            switch (algoritmo){
                case "Bubble Sort":
                    bubbleSort(arr, ascendente, velocidad);
                    break;
                case "Shell Sort":
                    shellSort(arr, ascendente, velocidad);
                    break;
                case "Quick Sort":
                    quickSort(arr, 0, arr.length - 1, ascendente, velocidad);
                    break;
            }

            long fin = System.currentTimeMillis();
            long tiempo = fin - inicio;
            agregarLog("[Fin] Ordenamiento completado en " + tiempo + " ms");
            System.out.println("Tiempo: " + tiempo + " ms");
          
            contadorEjecuciones++;
            Ejecucion e = new Ejecucion(contadorEjecuciones,algoritmo,ascendente ? "Ascendente" : "Descendente",arr.length,comparaciones,intercambios,iteraciones,tiempo);
            historial.add(e);
            generarReporteHTML(copiaOriginal,arr,algoritmo,ascendente ? "Ascendente" : "Descendente",comparaciones,intercambios,iteraciones,tiempo,vel);

            //Lo marca de verde
            for (int i = 0; i < arr.length; i++) {
                renderer.ordenado[i] = true;
            }

            int[] copia = arr.clone();
            SwingUtilities.invokeLater(() -> actualizarGrafica(copia));
            actualizarEstadisticas();
        }catch (Exception e) {
            e.printStackTrace();
        }

        SwingUtilities.invokeLater(() -> {
            jbtnIniciar.setEnabled(true);
        });

    }).start();
