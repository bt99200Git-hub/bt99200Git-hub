<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Votazione con Codici</title>
    <script>
        const codiciValidi = ["ABC123", "XYZ789", "QWE456"]; // Sostituisci con i tuoi codici
        let votiRegistrati = {};
        
        function verificaCodice() {
            const codiceInserito = document.getElementById("codice").value;
            if (codiciValidi.includes(codiceInserito) && !votiRegistrati[codiceInserito]) {
                document.getElementById("accesso").style.display = "none";
                document.getElementById("votazione").style.display = "block";
                sessionStorage.setItem("codice", codiceInserito);
            } else {
                alert("Codice non valido o già utilizzato.");
            }
        }
        
        function inviaVoto() {
            const codiceUsato = sessionStorage.getItem("codice");
            const voto = document.querySelector('input[name="voto"]:checked');
            if (voto) {
                votiRegistrati[codiceUsato] = voto.value;
                alert("Voto registrato con successo!");
                document.getElementById("votazione").style.display = "none";
            } else {
                alert("Seleziona un'opzione per votare.");
            }
        }
    </script>
</head>
<body>
    <div id="accesso">
        <h2>Inserisci il codice per votare</h2>
        <input type="text" id="codice" placeholder="Inserisci codice">
        <button onclick="verificaCodice()">Accedi</button>
    </div>
    
    <div id="votazione" style="display: none;">
        <h2>Esprimi il tuo voto</h2>
        <label><input type="radio" name="voto" value="Opzione 1"> Opzione 1</label><br>
        <label><input type="radio" name="voto" value="Opzione 2"> Opzione 2</label><br>
        <button onclick="inviaVoto()">Invia Voto</button>
    </div>
</body>
</html>
