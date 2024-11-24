<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <title>Modalverben-Spiel</title>
  <style>
    .dropzone {
      border: 2px dashed #ccc;
      padding: 20px;
      margin: 20px;
    }
    .draggable {
      padding: 10px;
      background: lightblue;
      margin: 5px;
      cursor: grab;
    }
  </style>
</head>
<body>
  <h1>Modalverben-Spiel</h1>
  <p>Ziehen Sie das passende Modalverb in die Lücke:</p>

  <div>
    <p>Ich <span class="dropzone" data-answer="kann"></span> Deutsch sprechen.</p>
    <p>Du <span class="dropzone" data-answer="musst"></span> die Hausaufgaben machen.</p>
  </div>

  <div id="options">
    <div class="draggable" draggable="true">kann</div>
    <div class="draggable" draggable="true">möchte</div>
    <div class="draggable" draggable="true">musst</div>
  </div>

  <script>
    const draggables = document.querySelectorAll(".draggable");
    const dropzones = document.querySelectorAll(".dropzone");

    draggables.forEach(item => {
      item.addEventListener("dragstart", e => {
        e.dataTransfer.setData("text", e.target.textContent);
      });
    });

    dropzones.forEach(zone => {
      zone.addEventListener("dragover", e => e.preventDefault());
      zone.addEventListener("drop", e => {
        const text = e.dataTransfer.getData("text");
        if (text === zone.getAttribute("data-answer")) {
          zone.textContent = text;
          zone.style.background = "lightgreen";
        } else {
          zone.style.background = "lightcoral";
        }
      });
    });
  </script>
</body>
</html>
