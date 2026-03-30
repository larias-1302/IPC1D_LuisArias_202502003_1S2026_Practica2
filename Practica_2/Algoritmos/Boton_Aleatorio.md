try{
        String input = JOptionPane.showInputDialog(this, "Ingrese cantidad (5-30):");

        if (input == null) return; //Se cancela
        int n = Integer.parseInt(input);

        if (n < 5 || n > 30) {
            JOptionPane.showMessageDialog(this, "Debe estar entre 5 y 30");
            return;
        }

        int[] arreglo = new int[n];

        for (int i = 0; i < n; i++) {
            arreglo[i] = (int)(Math.random() * 100);
        }

        //LLo guarda en el modelo
        datosModelo.setArreglo(arreglo);

        // Mostrar en el JTextField
        StringBuilder texto = new StringBuilder();

        for (int i = 0; i < arreglo.length; i++) {
            texto.append(arreglo[i]);
            if (i < arreglo.length - 1) {
                texto.append(",");
            }
        }

        jtxtDatos.setText(texto.toString());

    }catch (NumberFormatException e) {
        JOptionPane.showMessageDialog(this, "Ingrese un número válido");
    }
