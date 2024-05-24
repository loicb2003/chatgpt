<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tableau des Scores</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: Arial, sans-serif;
            background-color: #f5f5f5;
        }
        table {
            border-collapse: collapse;
            width: 80%;
            max-width: 1000px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 12px;
            text-align: center;
        }
        th {
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }
        tr:nth-child(even) {
            background-color: #f2f2f2;
        }
        .caller {
            font-weight: bold;
            color: #ff9933;
        }
        .manager, .director {
            color: #3366ff;
        }
        .highlight {
            background-color: #ffe066;
            font-weight: bold;
        }
        .highlight:hover {
            background-color: #ffd31a;
        }
    </style>
</head>
<body>
    <table id="scoreTable">
        <thead>
            <tr>
                <th onclick="sortTable(0)">Position</th>
                <th>Nom</th>
                <th>Arrivée à l'heure</th>
                <th>Appels Passés</th>
                <th>RDV fixés</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td class="highlight manager">-</td>
                <td class="highlight manager">Romain (Manager)</td>
                <td>-</td>
                <td>-</td>
                <td>20</td>
            </tr>
            <tr>
                <td class="highlight director">-</td>
                <td class="highlight director">Dorian (Directeur)</td>
                <td>-</td>
                <td>-</td>
                <td>15</td>
            </tr>
            <tr>
                <td>1</td>
                <td class="caller">Loic</td>
                <td>Oui</td>
                <td>50</td>
                <td>10</td>
            </tr>
            <tr>
                <td>2</td>
                <td class="caller">Kitan</td>
                <td>Oui</td>
                <td>45</td>
                <td>8</td>
            </tr>
            <tr>
                <td>3</td>
                <td class="caller">Omar</td>
                <td>Non</td>
                <td>55</td>
                <td>12</td>
            </tr>
            <tr>
                <td>4</td>
                <td class="caller">Jessy</td>
                <td>Oui</td>
                <td>60</td>
                <td>15</td>
            </tr>
            <tr>
                <td>5</td>
                <td class="caller">Harison</td>
                <td>Oui</td>
                <td>48</td>
                <td>9</td>
            </tr>
            <tr>
                <td>6</td>
                <td class="caller">Benjamin</td>
                <td>Non</td>
                <td>40</td>
                <td>7</td>
            </tr>
        </tbody>
    </table>
    <script>
        function sortTable(n) {
            let table, rows, switching, i, x, y, shouldSwitch, dir, switchcount = 0;
            table = document.getElementById("scoreTable");
            switching = true;
            dir = "asc"; 
            while (switching) {
                switching = false;
                rows = table.rows;
                for (i = 1; i < (rows.length - 1); i++) {
                    shouldSwitch = false;
                    x = rows[i].getElementsByTagName("TD")[n];
                    y = rows[i + 1].getElementsByTagName("TD")[n];
                    if (dir == "asc") {
                        if (x.innerHTML.toLowerCase() > y.innerHTML.toLowerCase()) {
                            shouldSwitch = true;
                            break;
                        }
                    } else if (dir == "desc") {
                        if (x.innerHTML.toLowerCase() < y.innerHTML.toLowerCase()) {
                            shouldSwitch = true;
                            break;
                        }
                    }
                }
                if (shouldSwitch) {
                    rows[i].parentNode.insertBefore(rows[i + 1], rows[i]);
                    switching = true;
                    switchcount++; 
                } else {
                    if (switchcount == 0 && dir == "asc") {
                        dir = "desc";
                        switching = true;
                    }
                }
            }
        }
    </script>
</body>
</html>
