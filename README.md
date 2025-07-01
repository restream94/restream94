<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>ESPN 2 - DASH ClearKey</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/shaka-player/4.3.5/shaka-player.compiled.js"></script>
</head>
<body style="margin:0;background:black;">
  <video id="video" width="100%" height="100%" controls autoplay></video>
  <script>
    async function initPlayer() {
      const manifestUri = "https://edge5-hr.cvattv.com.ar/.../ESPN2_Arg.mpd"; // Tu URL DASH completa
      const keyId = "65a5bfa3c7a72dde60be9b0c7406c8fc";
      const key = "0b40ae9f78a7bac3b57ecbf72d3c081e";

      shaka.polyfill.installAll();

      if (shaka.Player.isBrowserSupported()) {
        const video = document.getElementById('video');
        const player = new shaka.Player(video);

        player.configure({
          drm: {
            clearKeys: {
              [keyId]: key
            }
          },
          streaming: {
            alwaysStreamText: true
          }
        });

        try {
          await player.load(manifestUri);
        } catch (error) {
          console.error('Error loading video:', error);
        }
      } else {
        console.error('Shaka Player not supported');
      }
    }

    initPlayer();
  </script>
</body>
</html>
