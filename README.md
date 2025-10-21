<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Mapa de Valença - RJ</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- Importando o Leaflet -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css"/>
  <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

  <style>
    body { margin: 0; }
    #map {
      height: 100vh;
      width: 100%;
    }
  </style>
</head>

<body>
  <div id="map"></div>

  <script>
    // Coordenadas aproximadas de Valença - RJ
    var coordenadasValenca = [-22.2447, -43.7069];

    // Criação do mapa centrado em Valença
    var map = L.map('map').setView(coordenadasValenca, 13);

    // Adiciona o mapa base (OpenStreetMap)
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors'
    }).addTo(map);

    // Adiciona um marcador principal
    var marcador = L.marker(coordenadasValenca).addTo(map);
    marcador.bindPopup("<b>Valença - RJ</b><br>Cidade do interior do estado do Rio de Janeiro.").openPopup();

    // Evento: ao clicar no mapa, adiciona um novo marcador
    map.on('click', function(e) {
      L.marker(e.latlng).addTo(map)
        .bindPopup("Marcador em: " + e.latlng.toString())
        .openPopup();
    });
  </script>
</body>
</html>
