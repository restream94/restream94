<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Reproductor ESPN</title>
  <script src="https://cdn.dashjs.org/latest/dash.all.min.js"></script>
  <style>
    body { margin: 0; background: black; }
    video { width: 100vw; height: 100vh; }
  </style>
</head>
<body>
  <video id="videoPlayer" controls autoplay></video>
  <script>
    var url = "http://cdn.sensa.com.ar:80/live/eds/ESPN/live_dash_cld/ESPN.mpd";
    var player = dashjs.MediaPlayer().create();
    player.initialize(document.querySelector("#videoPlayer"), url, true);
  </script>
</body>
</html>
