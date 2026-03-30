JFileChooser fileChooser = new JFileChooser();
        int seleccion = fileChooser.showOpenDialog(this);

        if (seleccion == JFileChooser.APPROVE_OPTION) {
            File archivo = fileChooser.getSelectedFile();

            try{
                BufferedReader br = new BufferedReader(new FileReader(archivo));
                String linea;
                StringBuilder contenido = new StringBuilder();

                //Lee el archivo
                while ((linea = br.readLine()) != null) {
                    contenido.append(linea).append(",");
                }
                br.close();

                //Convierte el archivo en un arreglo
                String texto = contenido.toString();
                String[] partes = texto.split(",");                
                ArrayList<Integer> lista = new ArrayList<>();

                for (String p : partes) {
                    if (!p.trim().isEmpty()) {
                        lista.add(Integer.parseInt(p.trim()));
                    }
                }

                int[] arreglo = new int[lista.size()];
                for (int i = 0; i < lista.size(); i++) {
                    arreglo[i] = lista.get(i);
                }

                for (int i = 0; i < partes.length; i++) {
                    arreglo[i] = Integer.parseInt(partes[i].trim());
                }

                //Lo gudarda en el modelo
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
                JOptionPane.showMessageDialog(this, "Archivo cargado correctamente");

            }catch (Exception e) {
                JOptionPane.showMessageDialog(this, "Error al leer archivo");
                e.printStackTrace();
            }
        }
