<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Plastic Water Container</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background-image: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR6z8-gDFxK-sFpG0fwHDZVQTLbI930ioxKAg&s');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            backdrop-filter: brightness(0.8);
            color: #fff;
        }

        header {
            text-align: center;
            padding: 2rem 1rem 1rem 1rem;
            background-color: rgba(0, 0, 0, 0.6);
        }

        h1 {
            margin: 0;
            font-size: 2.5rem;
        }

        h2 {
            margin: 0.5rem 0 1rem;
            font-size: 1.5rem;
            color: #ffcc00;
        }

        .container {
            max-width: 1000px;
            margin: 2rem auto;
            background-color: rgba(255, 255, 255, 0.95);
            padding: 1rem;
            border-radius: 10px;
            color: #000;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1rem;
        }

        th, td {
            padding: 0.6rem;
            border: 1px solid #999;
            text-align: left;
        }

        th {
            background-color: #333;
            color: #fff;
        }

        tr.highlight {
            background-color: #ffff88;
        }

        .search-bar {
            display: flex;
            justify-content: center;
            gap: 0.5rem;
            margin-top: 1rem;
        }

        input[type="text"] {
            padding: 0.5rem;
            width: 250px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }

        button {
            padding: 0.5rem 1rem;
            border: none;
            background-color: #007bff;
            color: white;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background-color: #0056b3;
        }

        .page-link {
            display: block;
            text-align: center;
            margin: 2rem 0;
        }

        .page-link a {
            padding: 1rem;
            background-color: #007bff;
            color: white;
            text-decoration: none;
            border-radius: 5px;
        }

        .page-link a:hover {
            background-color: #0056b3;
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }
    </style>
</head>
<body>
    <header>
        <h1>Plastic Water Container</h1>
    </header>
    <div class="container">
        <div class="search-bar">
            <input type="text" id="searchInput" placeholder="Buscar código o clave...">
            <button onclick="searchCode()">Buscar</button>
        </div>
        <h2 style="margin-top: 1rem;">Inventario Completo</h2>
        <table id="inventoryTable">
            <thead>
                <tr>
                    <th>Cantidad de Stock</th>
                    <th>Descripción</th>
                    <th>Código o Clave</th>
                </tr>
            </thead>
            <tbody>
                <!-- Las filas serán agregadas dinámicamente con JavaScript -->
            </tbody>
        </table>
    </div>

    <script>
        const inventario = `CANTIDAD DE STOCK\tDESCRIPCION\tCODIGO O CLAVE
0\tchacis de carro\t1001002NA
2\tpieza plana en forma rectangular con 8 puntos de anclaje\t2002002NA
11\tpieza plana rectangular chica de 2 puntos de anclaje\t2003002NA
6\tpieza plana en forma de L de 3 puntos de anclaje\t2004002NA
5\tpieza plana cuadrada de 4 puntos de anclaje\t2005002NA
3\tpieza plana rectangular alargada de 4 puntos de anclaje\t2006002NA
8\tpieza plana de 1 punto de anclaje\t2007002NA
4\tpieza plana rectangular de 6 puntos de anclaje\t2008002NA
1\tpieza plana alargada de 6 puntos de anclaje\t2009002NA
2\tpieza plana de 1 punto de anclaje transparente\t2010002NA
2\tpieza plana lisa de color rojo de 1 puerto de anclaje\t3011002NA
2\tpieza plana liza en forma de pico\t3012002NA
2\tpieza plana liza en forma de pico\t3013002NA
2\tpieza liza en forma de rampa con 1 puerto de anclaje color rojo\t3014002NA
3\tpieza liza en forma de rampa con 2 puertos de anclaje color negro\t3015002NA
4\tpieza liza con una curba asia adelante con 4 puertos de anclaje en escalon\t3016002NA
6\tpieza liza en forma de rampa con un puerto de anclaje color negro\t3017002NA
1\tpieza liza cuadrada color negro con 4 puertos de anclaje\t3018002NA
2\tpieza liza con una curva asia adelante color negro con un logo inpreso de cuatro puertos de anclaje\t3019002NA
2\tpieza liza en forma de arco con un estampado\t3020002NA
2\tpieza liza alargada con una curba asia adelate de una sola fila de puertos de anclaje\t3021002NA
1\tpieza liza con una curva asia adelante color negro con un dos lineas rojas inpreso de cuatro puertos de anclaje\t3022002NA
2\tpieza liza alargada chica con una curva asia adelante con dos puertos de anclaje\t3023002NA
1\tpieza plana liza en forma de pico color negro\t3024002RH
1\tpieza plana liza en forma de pico color negro\t3025002LH
1\tpieza liza con un logo estampado\t3026002NA
1\tpieza liza con una curba asia adelante con dos lineas rojas que llegan a la mitad de la pieza\t3027002NA
2\tpieza liza en forma de rampa transparente con 1 puerto de anclaje\t3028002NA
1\tpieza liza en forma de rampa con 2 puertos de anclaje de color gris\t3029002NA
1\tpieza liza de color negre de 6 puertos de anclaje\t3030002NA
2\t´pieza liza en forma de L con la esquina cortada\t3031002NA
2\tpieza liza alargada de color negro con una curba asia adelate de una sola fila de puertos de anclaje\t3032002NA
4\tpieza en forma de L vertical con 2 puertos de anclaje y 4 puntos de anclaje\t4033002NA
4\tpieza cuadrada con un escalon y un pequeño eje en un extremo\t4034002NA
2\tpieza de un solo puerto de anclaje con dos paredes en forma de L\t4035002NA
1\tpieza en forma de volante de auto\t4036002NA
4\tpiesa con 4 puntos de anclaje con un escalon con un arco en un extremo\t4037002NA
4\tpieza cubica con un saliente en su parte inferior un punto de anclaje arriba y uno en un extremo\t4038002NA
1\tpieza de 2 puntos de anclaje con 2 ganchos en un extremo\t4039002NA
3\tpieza en forma de L vertical con 2 puertos de anclaje y 4 puntos de anclaje( invertida )\t4040002NA
4\tpieza cubica con 1 punto de anclaje arriba y uno en un extremo los puntos son huecos\t4041002NA
2\tpiesa en forma de rampa en el sentro es escalonada de color rojo\t4042002NA
2\tpieza con un punto de anclaje y un eje orizontal con dos puntos de anclajes huecos\t4043002NA
2\tpieza con 2 puertos de anclaje con un perfil en un extremo\t4044002NA
2\tpieza cubica con un punto de anclaje\t4045002NA
2\tpieza de 2 puntos de anclaje huecos y un puerto de anclaje de forma horizontal\t4046002NA
1\tpieza de 2 puntos de anclaje y un anclaje vertical\t4047002NA
2\tpieza en forma de rampa alargada con dos puntos de anclaje huecos en el lugar de los puertos\t4048002NA
2\tpieza liza con un puerto de anclaje con la esquina redondeada\t4049002NA
2\tpiesa en forma de rampa en el sentro es escalonada de color negro\t4050002NA
1\tpieza en forma de L en vertical con dos abrasaderas a los costados\t4051002NA
1\tpieza cuadrada con una esquina cortada de color rojo transparente con tres puertos de anclaje\t4052002RH
1\tpieza cuadrada con una esquina cortada de color rojo transparente con tres puertos de anclaje\t4053002LH
3\tpieza en forma de aleron pequeño\t4054002NA
4\tpieza cilindrica con un hueco en el centro(rin de rueda)\t4055002NA
4\tpieza circular con un hueco muy grande en el centro en el exterior tiene dientes (rueda de carro )\t4056002NA
1\tpiesa grande en forma de rampa curviada asia adelante transparente ( para brisas de carro)\t4057002NA`;

        const tbody = document.querySelector("#inventoryTable tbody");
        const lineas = inventario.split("\n").slice(1);
        for (const linea of lineas) {
            const [cantidad, descripcion, codigo] = linea.split("\t");
            const tr = document.createElement("tr");
            tr.innerHTML = `<td>${cantidad}</td><td>${descripcion}</td><td>${codigo}</td>`;
            tbody.appendChild(tr);
        }

        function searchCode() {
            const input = document.getElementById("searchInput").value.trim().toLowerCase();
            const filas = document.querySelectorAll("#inventoryTable tbody tr");

            let found = false;

            filas.forEach(tr => {
                tr.classList.add("highlight");
                const codigo = tr.children[2].textContent.toLowerCase();
                if (codigo === input) {
                    tr.classList.add("highlight");
                    tr.scrollIntoView({ behavior: "smooth", block: "center" });
                    found = true;
                }
            });

            if (!found && input !== "") {
                alert("Código no encontrado.");
            }
        }

        document.getElementById("searchInput").addEventListener("keydown", function(e) {
            if (e.key === "Enter") {
                searchCode();
            }
        });
    </script>
</body>
</html>
