fetch("deine_datei.csv")
  .then(response => response.text())
  .then(text => {
    const zeilen = text.split("\n");
    let woerterbuch = {};

    // Erste Zeile (Überschrift) überspringen
    for (let i = 1; i < zeilen.length; i++) {
      const spalten = zeilen[i].split(",");
      if (spalten.length >= 2) {
        const key = spalten[0].trim();
        const value = spalten[1].trim();
        woerterbuch[key] = value;
      }
    }
    
    // Jetzt hast du wieder dein gewohntes JSON-Objekt im Speicher!
    console.log(woerterbuch); 
  });
