try{
        String texto = jtxtDatos.getText().trim();

        if (texto.isEmpty()) {
            JOptionPane.showMessageDialog(this, "Ingrese datos primero");
            return;
        }

        //Separar por comas o saltos de línea
        String[] partes = texto.split("[,\\n]");
        int[] arreglo = new int[partes.length];

        for (int i = 0; i < partes.length; i++) {
            arreglo[i] = Integer.parseInt(partes[i].trim());
        }

        //Lo guarda en el modelo
        datosModelo.setArreglo(arreglo);
        
        //Reestablece mi renderer
        renderer = new CustomRenderer(arreglo.length);
        chart.getCategoryPlot().setRenderer(renderer);
        renderer.comp1 = -1;
        renderer.comp2 = -1;
        renderer.swap1 = -1;
        renderer.swap2 = -1;
        renderer.ordenado = new boolean[arreglo.length];
        
        //Actualiza la grafica
        actualizarGrafica(arreglo);
        JOptionPane.showMessageDialog(this, "Datos cargados correctamente");

        }catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Error: solo números separados por comas");
        }
