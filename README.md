<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title>Front Camera (with permission)</title>
</head>
<body>
  <video id="preview" autoplay playsinline></video>
  <button id="start">Start (asks permission)</button>
  <script>
    document.getElementById('start').onclick = async () => {
      try {
        const stream = await navigator.mediaDevices.getUserMedia({
          video: { facingMode: "user" }, audio: false
        });
        document.getElementById('preview').srcObject = stream;
      } catch (err) {
        console.error("User denied or no camera available:", err);
      }
    };
  </script>
</body>
</html>
