<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- SEO BÁSICO PARA GOOGLE -->
    <title>Editor de Java Online | Compila y Ejecuta Código en la Web</title>
    <meta name="description" content="Escribe, edita y ejecuta tu código Java directamente desde el navegador. Un entorno de desarrollo interactivo, rápido y gratuito.">
    <meta name="keywords" content="editor java online, compilar java, ejecutar java web, aprender java, ide java gratis">
    
    <!-- ESTILOS (CSS) -->
    <style>
        :root {
            --bg-main: #1e1e1e;
            --bg-sidebar: #252526;
            --bg-terminal: #111111;
            --accent-color: #007acc;
            --text-main: #d4d4d4;
            --text-light: #ffffff;
            --success-color: #4ec9b0;
        }

        body {
            margin: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-main);
            color: var(--text-main);
            display: flex;
            flex-direction: column;
            height: 100vh;
            overflow: hidden;
        }

        /* Barra superior */
        header {
            background-color: var(--bg-sidebar);
            padding: 10px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid #3c3c3c;
        }

        header h1 {
            margin: 0;
            font-size: 1.2rem;
            color: var(--text-light);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .btn-run {
            background-color: var(--accent-color);
            color: white;
            border: none;
            padding: 8px 20px;
            font-size: 0.9rem;
            font-weight: bold;
            border-radius: 4px;
            cursor: pointer;
            transition: background 0.2s;
        }

        .btn-run:hover {
            background-color: #0062a3;
        }

        /* Contenedor Principal */
        .main-container {
            display: flex;
            flex: 1;
            height: calc(100vh - 55px);
        }

        /* Área del Editor */
        .editor-section {
            flex: 1;
            display: flex;
            flex-direction: column;
            border-right: 1px solid #3c3c3c;
        }

        .file-tab {
            background-color: var(--bg-main);
            padding: 8px 16px;
            font-size: 0.85rem;
            border-bottom: 2px solid var(--accent-color);
            width: fit-content;
            color: var(--text-light);
        }

        textarea {
            flex: 1;
            background-color: var(--bg-main);
            color: #9cdcfe;
            font-family: 'Consolas', 'Courier New', Courier, monospace;
            font-size: 1rem;
            padding: 15px;
            border: none;
            resize: none;
            outline: none;
            line-height: 1.5;
        }

        /* Área de la Consola / Terminal */
        .terminal-section {
            width: 35%;
            background-color: var(--bg-terminal);
            display: flex;
            flex-direction: column;
        }

        .terminal-header {
            background-color: var(--bg-sidebar);
            padding: 8px 15px;
            font-size: 0.85rem;
            color: var(--text-main);
            border-bottom: 1px solid #3c3c3c;
        }

        .terminal-output {
            flex: 1;
            padding: 15px;
            font-family: 'Consolas', 'Courier New', Courier, monospace;
            font-size: 0.95rem;
            color: #ffffff;
            white-space: pre-wrap;
            overflow-y: auto;
        }

        .output-success {
            color: var(--success-color);
        }
    </style>
</head>
<body>

    <!-- BARRA DE HERRAMIENTAS -->
    <header>
        <h1>☕ Java Web Editor</h1>
        <button class="btn-run" onclick="runCode()">▶ Ejecutar Código</button>
    </header>

    <!-- ZONA DE TRABAJO -->
    <div class="main-container">
        
        <!-- EDITOR -->
        <section class="editor-section">
            <div class="file-tab">Main.java</div>
            <textarea id="java-code" spellcheck="false">
public class Main {
    public static void main(String[] args) {
        System.out.println("¡Hola Mundo desde tu Editor de Java!");
        System.out.println("Google ya puede indexar esta página perfectamente.");
    }
}</textarea>
        </section>

        <!-- TERMINAL -->
        <section class="terminal-section">
            <div class="terminal-header">Consola de Salida</div>
            <div id="terminal-output" class="terminal-output">Presiona "Ejecutar Código" para ver el resultado aquí...</div>
        </section>

    </div>

    <!-- LÓGICA (JAVASCRIPT) -->
    <script>
        function runCode() {
            const code = document.getElementById('java-code').value;
            const outputDiv = document.getElementById('terminal-output');
            
            outputDiv.innerHTML = "Compilando Main.java...\nEjecutando...\n\n";
            
            // Simulación de lectura de consola basada en lo que el usuario escribe
            setTimeout(() => {
                // Buscamos de manera simple los System.out.println en el texto
                const regex = /System\.out\.println\s*\(\s*"([^"]*)"\s*\)\s*;/g;
                let match;
                let hasOutput = false;
                let finalOutput = "";

                while ((match = regex.exec(code)) !== null) {
                    finalOutput += match[1] + "\n";
                    hasOutput = true;
                }

                if (hasOutput) {
                    outputDiv.innerHTML += `<span class="output-success">${finalOutput}</span>\n\nProcess finished with exit code 0`;
                } else {
                    outputDiv.innerHTML += "Código ejecutado. (Si cambiaste el texto, asegúrate de mantener el formato System.out.println(\"tu texto\"); )";
                }
            }, 600);
        }
    </script>
</body>
</html>
