# Applicazione Generatore File Verifica Massiva IRM

Copia integralmente il codice HTML qui sotto e salvalo come file `.html` per creare l'applicazione.

```html
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Generatore File Verifica Massiva - IRM</title>
    <style>
        * {
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            margin: 0;
            padding: 20px;
            min-height: 100vh;
        }
        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }
        .header {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: white;
            padding: 25px 30px;
            text-align: center;
        }
        .header h1 {
            margin: 0;
            font-size: 1.8em;
        }
        .header p {
            margin: 10px 0 0;
            opacity: 0.9;
            font-size: 0.9em;
        }
        .content {
            padding: 30px;
        }
        .section {
            background: #f8f9fa;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 25px;
            border: 1px solid #e0e0e0;
        }
        .section-title {
            font-size: 1.3em;
            font-weight: 600;
            color: #2a5298;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 2px solid #2a5298;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .form-group {
            margin-bottom: 20px;
        }
        label {
            display: block;
            font-weight: 600;
            margin-bottom: 8px;
            color: #333;
        }
        input, textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 14px;
            font-family: monospace;
            transition: border-color 0.3s;
        }
        input:focus, textarea:focus {
            outline: none;
            border-color: #2a5298;
            box-shadow: 0 0 0 3px rgba(42,82,152,0.1);
        }
        input.valid {
            border-color: #28a745;
            background-color: #f0fff4;
        }
        input.invalid {
            border-color: #dc3545;
            background-color: #fff8f8;
        }
        textarea {
            font-family: 'Courier New', monospace;
            font-size: 12px;
            resize: vertical;
        }
        .error-message {
            color: #dc3545;
            font-size: 12px;
            margin-top: 5px;
            display: block;
        }
        .valid-message {
            color: #28a745;
            font-size: 12px;
            margin-top: 5px;
            display: block;
        }
        .help-text {
            color: #666;
            font-size: 12px;
            margin-top: 5px;
            display: block;
        }
        .button-group {
            display: flex;
            gap: 15px;
            margin-top: 20px;
            flex-wrap: wrap;
        }
        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 14px;
        }
        .btn-primary {
            background: linear-gradient(135deg, #2a5298, #1e3c72);
            color: white;
        }
        .btn-primary:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(42,82,152,0.3);
        }
        .btn-primary:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        .btn-success {
            background: linear-gradient(135deg, #11998e, #38ef7d);
            color: white;
        }
        .btn-success:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(17,153,142,0.3);
        }
        .btn-secondary {
            background: #6c757d;
            color: white;
        }
        .btn-secondary:hover {
            background: #5a6268;
        }
        .btn-danger {
            background: #28a745;
            color: white;
        }
        .btn-danger:hover:not(:disabled) {
            background: #218838;
            transform: translateY(-2px);
        }
        .btn-danger:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        .preview {
            background: #1e1e1e;
            color: #d4d4d4;
            padding: 20px;
            border-radius: 8px;
            font-family: 'Courier New', monospace;
            font-size: 12px;
            overflow-x: auto;
            max-height: 500px;
            white-space: pre;
        }
        .stats {
            background: #e8f4f8;
            padding: 15px;
            border-radius: 8px;
            margin-top: 15px;
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
        }
        .stat-item {
            flex: 1;
            text-align: center;
            padding: 10px;
            background: white;
            border-radius: 8px;
        }
        .stat-label {
            font-size: 12px;
            color: #666;
            text-transform: uppercase;
        }
        .stat-value {
            font-size: 24px;
            font-weight: bold;
            color: #2a5298;
        }
        .alert-success {
            background: #d4edda;
            color: #155724;
            padding: 12px;
            border-radius: 8px;
            margin-bottom: 15px;
            border: 1px solid #c3e6cb;
        }
        .alert-error {
            background: #f8d7da;
            color: #721c24;
            padding: 12px;
            border-radius: 8px;
            margin-bottom: 15px;
            border: 1px solid #f5c6cb;
        }
        .table-wrapper {
            overflow-x: auto;
            max-height: 500px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 12px;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: left;
        }
        th {
            background: #2a5298;
            color: white;
            position: sticky;
            top: 0;
        }
        tr:nth-child(even) {
            background: #f9f9f9;
        }
        .footer {
            background: #f8f9fa;
            padding: 15px 30px;
            text-align: center;
            font-size: 12px;
            color: #666;
            border-top: 1px solid #e0e0e0;
        }
        .format-example {
            background: #e9ecef;
            padding: 10px;
            border-radius: 6px;
            font-family: monospace;
            font-size: 12px;
            margin-top: 8px;
        }
        .cf-warning {
            background: #fff3cd;
            border: 1px solid #ffc107;
            border-radius: 6px;
            padding: 10px;
            margin-top: 10px;
            font-size: 12px;
        }
        .record-detail {
            font-family: monospace;
            font-size: 11px;
            background: #f0f0f0;
            padding: 8px;
            border-radius: 4px;
            margin-top: 5px;
            line-height: 1.6;
        }
        .data-editor {
            background: #fff;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 15px;
            margin-top: 15px;
        }
        .data-editor h4 {
            margin: 0 0 10px 0;
            color: #2a5298;
        }
        .btn-small {
            padding: 5px 10px;
            font-size: 11px;
            margin-left: 10px;
        }
        @media (max-width: 768px) {
            .content {
                padding: 15px;
            }
            .button-group {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>📄 Verifica delle Inadempienze</h1>
            <p>Generatore Flussi Massivi di Verifica - Conforme alle specifiche IRM (Lunghezza Record 300 byte)</p>
            <p style="font-size: 12px; margin-top: 5px;">✅ Progressivo Record incrementale | Progressivo Richiesta = 0000001 per ogni RMD | CF allineato a sinistra su 16 caratteri con spazi a destra</p>
        </div>
        
        <div class="content">
            <!-- Messaggi -->
            <div id="successMessage" style="display: none;" class="alert-success"></div>
            <div id="errorMessage" style="display: none;" class="alert-error"></div>

            <!-- Sezione Editor Dati Fornitori -->
            <div class="section">
                <div class="section-title">
                    <span>✏️</span> Editor Dati Fornitori
                    <button class="btn-small btn-secondary" onclick="addSupplierRow()" style="margin-left: auto;">➕ Aggiungi Fornitore</button>
                </div>
                <div class="table-wrapper">
                    <table id="supplierTable">
                        <thead>
                            <tr>
                                <th style="width: 40px;">#</th>
                                <th>Codice Fornitore</th>
                                <th>Descrizione</th>
                                <th>Codice Fiscale</th>
                                <th>Importo Lordo (€)</th>
                                <th style="width: 60px;">Azioni</th>
                            </tr>
                        </thead>
                        <tbody id="supplierTableBody">
                        </tbody>
                    </table>
                </div>
                <div class="cf-warning">
                    <strong>ℹ️ Nota sui Codici Fiscali:</strong><br>
                    Secondo le specifiche, il campo "CODICE FISCALE DEL BENEFICIARIO" (posizioni 19-34) deve avere <strong>lunghezza 16 caratteri</strong>.<br>
                    I CF con meno di 16 caratteri vengono automaticamente allineati a sinistra e completati con spazi a destra.
                </div>
            </div>

            <!-- Sezione Configurazione File -->
            <div class="section">
                <div class="section-title">
                    <span>⚙️</span> Configurazione File di Richiesta
                </div>
                
                <div class="form-group">
                    <label>📁 Nome File <span style="color: red;">*</span></label>
                    <input type="text" id="filename" value="IRMEQS20250000000001.TXT" oninput="validateFilename()" onchange="validateFilename()">
                    <div class="help-text">Formato obbligatorio: <strong>IRMEQSaaaaNNNNNNNNNN.TXT</strong></div>
                    <div class="format-example">
                        <strong>✅ Esempi validi:</strong><br>
                        • IRMEQS20250000000001.TXT<br>
                        • IRMEQS20250000012345.TXT<br><br>
                        <strong>❌ Esempi NON validi:</strong><br>
                        • IRMEQS2025000000001.TXT (solo 9 cifre progressivo)<br>
                        • IRM20250000000001.TXT (manca EQS)
                    </div>
                    <div id="filenameError" class="error-message" style="display: none;"></div>
                    <div id="filenameValid" class="valid-message" style="display: none;">✅ Formato nome file valido</div>
                </div>
                
                <div class="form-group">
                    <label>📅 Data Creazione File (AAAAMMGG)</label>
                    <input type="text" id="creationDate" maxlength="8" placeholder="AAAA MM GG">
                    <div class="help-text">Formato: anno (4 cifre) + mese (2 cifre) + giorno (2 cifre) es: 20250324</div>
                </div>
                
                <div class="button-group">
                    <button class="btn btn-primary" onclick="generateAndPreview()" id="generateBtn">🚀 Genera e Anteprima</button>
                    <button class="btn btn-danger" onclick="downloadFile()" id="downloadBtn" disabled>💾 Scarica File TXT</button>
                    <button class="btn btn-secondary" onclick="resetForm()">🔄 Reset</button>
                    <button class="btn btn-secondary" onclick="loadExampleData()">📋 Carica Esempio</button>
                </div>
            </div>

            <!-- Sezione Anteprima -->
            <div class="section" id="previewSection" style="display: none;">
                <div class="section-title">
                    <span>📄</span> Anteprima del File Generato
                </div>
                <div class="preview" id="previewContent"></div>
            </div>

            <!-- Sezione Statistiche -->
            <div class="section" id="statsSection" style="display: none;">
                <div class="section-title">
                    <span>📈</span> Statistiche del File
                </div>
                <div class="stats" id="statsContent"></div>
            </div>

            <!-- Sezione Dettaglio Record -->
            <div class="section" id="detailSection" style="display: none;">
                <div class="section-title">
                    <span>🔍</span> Dettaglio Record Generati
                </div>
                <div id="detailContent" class="record-detail"></div>
            </div>
        </div>
        
        <div class="footer">
            <p>Conforme alle specifiche del manuale "Verifica Massiva - User Guide 6.5"</p>
            <p>Record di Testa (RMA) - Record Richiesta (RMD) - Record di Coda (RMZ) | Lunghezza record: 300 byte</p>
            <p>✅ Codice Fiscale: allineato a sinistra su 16 caratteri con spazi a destra | Tipo Soggetto = 2 (persona giuridica)</p>
        </div>
    </div>

    <script>
        // Array dei fornitori - modificabile dall'utente
        let suppliersData = [];

        // Dati di esempio
        const exampleData = [
            { cod_fornitore: "F0059648", descrizione: "DIEMME S.R.L. DISPOSITIVI MEDICI", cf: "11873880154", importo_lordo: 6803 },
            { cod_fornitore: "F0011177", descrizione: "BOSTON SCIENTIFIC S.P.A.", cf: "11206730159", importo_lordo: 18798 },
            { cod_fornitore: "F0060904", descrizione: "BIOTRONIK ITALIA S.P.A.", cf: "09699320017", importo_lordo: 11273 }
        ];

        let generatedContent = null;
        let generatedRecords = [];

        // Carica i dati di esempio all'avvio
        function loadExampleData() {
            suppliersData = JSON.parse(JSON.stringify(exampleData));
            renderSupplierTable();
            showMessage('✅ Dati di esempio caricati con successo!');
        }

        // Renderizza la tabella dei fornitori
        function renderSupplierTable() {
            const tbody = document.getElementById('supplierTableBody');
            tbody.innerHTML = '';
            suppliersData.forEach((supplier, index) => {
                const row = tbody.insertRow();
                row.insertCell(0).textContent = index + 1;
                row.insertCell(1).innerHTML = `<input type="text" value="${escapeHtml(supplier.cod_fornitore)}" style="width:100%; padding:4px;" onchange="updateSupplier(${index}, 'cod_fornitore', this.value)">`;
                row.insertCell(2).innerHTML = `<input type="text" value="${escapeHtml(supplier.descrizione)}" style="width:100%; padding:4px;" onchange="updateSupplier(${index}, 'descrizione', this.value)">`;
                row.insertCell(3).innerHTML = `<input type="text" value="${escapeHtml(supplier.cf)}" style="width:100%; padding:4px;" onchange="updateSupplier(${index}, 'cf', this.value)">`;
                row.insertCell(4).innerHTML = `<input type="number" step="0.01" value="${supplier.importo_lordo}" style="width:100%; padding:4px;" onchange="updateSupplier(${index}, 'importo_lordo', parseFloat(this.value))">`;
                row.insertCell(5).innerHTML = `<button class="btn-small" style="background:#dc3545; color:white; border:none; border-radius:4px; cursor:pointer;" onclick="deleteSupplier(${index})">🗑️</button>`;
                
                // Evidenzia CF con lunghezza diversa da 16
                if (supplier.cf.length !== 16) {
                    row.style.backgroundColor = '#fff3cd';
                } else {
                    row.style.backgroundColor = '';
                }
            });
        }

        // Funzione di escape per evitare injection
        function escapeHtml(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }

        // Aggiorna un fornitore
        function updateSupplier(index, field, value) {
            if (suppliersData[index]) {
                suppliersData[index][field] = value;
                renderSupplierTable();
            }
        }

        // Elimina un fornitore
        function deleteSupplier(index) {
            if (confirm('Eliminare questo fornitore?')) {
                suppliersData.splice(index, 1);
                renderSupplierTable();
                showMessage('✅ Fornitore eliminato');
            }
        }

        // Aggiungi un nuovo fornitore
        function addSupplierRow() {
            suppliersData.push({
                cod_fornitore: "F0000000",
                descrizione: "NUOVO FORNITORE S.R.L.",
                cf: "00000000000",
                importo_lordo: 0
            });
            renderSupplierTable();
            showMessage('✅ Nuovo fornitore aggiunto. Modifica i dati nella tabella.');
        }

        // Validazione nome file secondo specifiche
        function validateFilename() {
            const filename = document.getElementById('filename').value.trim();
            const filenameRegex = /^IRMEQS[0-9]{4}[0-9]{10}\.TXT$/i;
            const errorDiv = document.getElementById('filenameError');
            const validDiv = document.getElementById('filenameValid');
            const generateBtn = document.getElementById('generateBtn');
            const filenameInput = document.getElementById('filename');
            
            if (!filenameRegex.test(filename.toUpperCase())) {
                errorDiv.style.display = 'block';
                errorDiv.textContent = '❌ Formato nome file non valido. Deve essere: IRMEQS + ANNO(4 cifre) + PROGRESSIVO(10 cifre) + .TXT';
                validDiv.style.display = 'none';
                generateBtn.disabled = true;
                filenameInput.classList.remove('valid');
                filenameInput.classList.add('invalid');
                return false;
            } else {
                errorDiv.style.display = 'none';
                validDiv.style.display = 'block';
                generateBtn.disabled = false;
                filenameInput.classList.remove('invalid');
                filenameInput.classList.add('valid');
                return true;
            }
        }

        // Formatta stringa con lunghezza fissa (allineamento a sinistra con spazi a destra)
        function formatString(str, length) {
            let result = String(str || '');
            if (result.length > length) {
                return result.substring(0, length);
            }
            return result.padEnd(length, ' ');
        }

        // Formatta numero con lunghezza fissa (allineamento a destra con zeri)
        function formatNumber(num, length) {
            return String(num).padStart(length, '0');
        }

        // Formatta importo in centesimi
        function formatAmount(amount, length) {
            const value = Math.round(amount * 100);
            return String(value).padStart(length, '0');
        }

        // Genera identificativo file
        function generateFileIdentifier(filename) {
            const baseName = filename.toUpperCase().replace(/\.TXT$/i, '');
            return baseName;
        }

        // Genera il file
        function generateFile() {
            if (!validateFilename()) {
                return null;
            }
            
            if (suppliersData.length === 0) {
                showMessage('❌ Nessun fornitore presente. Aggiungi almeno un fornitore.', true);
                return null;
            }
            
            const filename = document.getElementById('filename').value.trim();
            let creationDate = document.getElementById('creationDate').value.trim();
            
            if (!creationDate) {
                const now = new Date();
                creationDate = now.getFullYear() + 
                              String(now.getMonth() + 1).padStart(2, '0') + 
                              String(now.getDate()).padStart(2, '0');
                document.getElementById('creationDate').value = creationDate;
            }
            
            const fileIdentifier = generateFileIdentifier(filename);
            let records = [];
            let recordCounter = 1;
            
            // Record di Testa RMA
            let rmaRecord = '';
            rmaRecord += formatString('RMA', 3);
            rmaRecord += formatNumber(recordCounter, 7);
            rmaRecord += formatString(fileIdentifier, 20);
            rmaRecord += formatString(creationDate, 8);
            rmaRecord += formatString('R01', 3);
            rmaRecord += formatString('', 259);
            records.push({
                type: 'RMA',
                content: rmaRecord,
                counter: recordCounter
            });
            recordCounter++;
            
            // Record RMD per ogni fornitore
            suppliersData.forEach((supplier, idx) => {
                let rmdRecord = '';
                rmdRecord += formatString('RMD', 3);                        // Tipo Record (pos 1-3)
                rmdRecord += formatNumber(recordCounter, 7);                // Progressivo Record (pos 4-10)
                rmdRecord += formatNumber(1, 7);                            // Progressivo Richiesta (pos 11-17) = 0000001
                rmdRecord += formatString('2', 1);                          // Tipo Soggetto (pos 18) = 2 (persona giuridica)
                rmdRecord += formatString(supplier.cf, 16);                 // Codice Fiscale (pos 19-34)
                rmdRecord += formatString(supplier.cod_fornitore, 15);      // Identificativo Pagamento (pos 35-49)
                rmdRecord += formatAmount(supplier.importo_lordo, 15);      // Importo Titolo (pos 50-64)
                rmdRecord += formatString('', 35);                          // Indirizzo Beneficiario (blank)
                rmdRecord += formatString('', 5);                           // Numero Civico (blank)
                rmdRecord += formatString('', 5);                           // CAP (blank)
                rmdRecord += formatString('', 2);                           // Sigla Provincia (blank)
                rmdRecord += formatString('', 50);                          // Descrizione Comune (blank)
                rmdRecord += formatString('', 12);                          // Num. Tel. (blank)
                rmdRecord += formatString('', 35);                          // Cognome Referente (blank)
                rmdRecord += formatString('', 35);                          // Nome Referente (blank)
                rmdRecord += formatString('', 57);                          // Filler (pos 244-300)
                records.push({
                    type: 'RMD',
                    content: rmdRecord,
                    counter: recordCounter,
                    supplier: supplier,
                    cfPadded: formatString(supplier.cf, 16)
                });
                recordCounter++;
            });
            
            // Record di Coda RMZ
            let rmzRecord = '';
            rmzRecord += formatString('RMZ', 3);
            rmzRecord += formatNumber(recordCounter, 7);
            rmzRecord += formatString(fileIdentifier, 20);
            rmzRecord += formatString(creationDate, 8);
            rmzRecord += formatNumber(recordCounter, 7);
            rmzRecord += formatString('', 255);
            records.push({
                type: 'RMZ',
                content: rmzRecord,
                counter: recordCounter,
                totalRecords: recordCounter
            });
            
            generatedRecords = records;
            return records.map(r => r.content).join('\n');
        }

        // Mostra messaggio
        function showMessage(text, isError = false) {
            const msgDiv = isError ? document.getElementById('errorMessage') : document.getElementById('successMessage');
            msgDiv.textContent = text;
            msgDiv.style.display = 'block';
            setTimeout(() => {
                msgDiv.style.display = 'none';
            }, 5000);
        }

        // Genera e mostra anteprima
        function generateAndPreview() {
            if (!validateFilename()) {
                showMessage('❌ Correggi il nome file prima di procedere', true);
                return;
            }
            
            if (suppliersData.length === 0) {
                showMessage('❌ Aggiungi almeno un fornitore nella tabella sopra', true);
                return;
            }
            
            generatedContent = generateFile();
            
            if (!generatedContent) {
                return;
            }
            
            // Abilita download
            document.getElementById('downloadBtn').disabled = false;
            
            showMessage('✅ File generato con successo! Clicca su "Scarica File TXT" per salvarlo.');
            
            // Calcola statistiche
            const lines = generatedContent.split('\n');
            const rmaCount = lines.filter(l => l.substring(0,3) === 'RMA').length;
            const rmdCount = lines.filter(l => l.substring(0,3) === 'RMD').length;
            const rmzCount = lines.filter(l => l.substring(0,3) === 'RMZ').length;
            const allValid = lines.every(l => l.length === 300);
            
            // Mostra statistiche
            const statsSection = document.getElementById('statsSection');
            const statsContent = document.getElementById('statsContent');
            statsContent.innerHTML = `
                <div class="stat-item"><div class="stat-label">RMA (Testa)</div><div class="stat-value">${rmaCount}</div></div>
                <div class="stat-item"><div class="stat-label">RMD (Richieste)</div><div class="stat-value">${rmdCount}</div></div>
                <div class="stat-item"><div class="stat-label">RMZ (Coda)</div><div class="stat-value">${rmzCount}</div></div>
                <div class="stat-item"><div class="stat-label">Totale Record</div><div class="stat-value">${lines.length}</div></div>
                <div class="stat-item"><div class="stat-label">Lunghezza</div><div class="stat-value">${allValid ? '300 byte ✓' : 'ERRORE'}</div></div>
            `;
            statsSection.style.display = 'block';
            
            // Mostra dettaglio record
            const detailSection = document.getElementById('detailSection');
            const detailContent = document.getElementById('detailContent');
            let detailHtml = '<strong>📋 Struttura completa dei record generati:</strong><br><br>';
            
            generatedRecords.forEach(rec => {
                if (rec.type === 'RMA') {
                    detailHtml += `<span style="color:#2a5298;">🔷 RMA (Record di Testa)</span><br>`;
                    detailHtml += `&nbsp;&nbsp;Progressivo Record: ${rec.counter.toString().padStart(7, '0')}<br>`;
                    detailHtml += `&nbsp;&nbsp;Identificativo File: ${rec.content.substring(10, 30).trim()}<br>`;
                    detailHtml += `&nbsp;&nbsp;Data Creazione: ${rec.content.substring(30, 38)}<br><br>`;
                } else if (rec.type === 'RMD') {
                    detailHtml += `<span style="color:#28a745;">🟢 RMD (Record Richiesta) - Fornitore: ${rec.supplier.cod_fornitore}</span><br>`;
                    detailHtml += `&nbsp;&nbsp;Progressivo Record: ${rec.counter.toString().padStart(7, '0')}<br>`;
                    detailHtml += `&nbsp;&nbsp;Progressivo Richiesta: 0000001<br>`;
                    detailHtml += `&nbsp;&nbsp;Tipo Soggetto: 2 (Persona Giuridica)<br>`;
                    detailHtml += `&nbsp;&nbsp;Codice Fiscale Originale: "${rec.supplier.cf}" (${rec.supplier.cf.length} caratteri)<br>`;
                    detailHtml += `&nbsp;&nbsp;Codice Fiscale con Padding: "${rec.cfPadded}" (16 caratteri)<br>`;
                    detailHtml += `&nbsp;&nbsp;Identificativo Pagamento: ${rec.supplier.cod_fornitore}<br>`;
                    detailHtml += `&nbsp;&nbsp;Importo Lordo: € ${rec.supplier.importo_lordo.toFixed(2)} → ${formatAmount(rec.supplier.importo_lordo, 15)} (in centesimi)<br><br>`;
                } else if (rec.type === 'RMZ') {
                    detailHtml += `<span style="color:#dc3545;">🔴 RMZ (Record di Coda)</span><br>`;
                    detailHtml += `&nbsp;&nbsp;Progressivo Record: ${rec.counter.toString().padStart(7, '0')}<br>`;
                    detailHtml += `&nbsp;&nbsp;Totale Record nel file: ${rec.totalRecords.toString().padStart(7, '0')}<br>`;
                    detailHtml += `&nbsp;&nbsp;Identificativo File: ${rec.content.substring(10, 30).trim()}<br>`;
                }
            });
            
            detailContent.innerHTML = detailHtml;
            detailSection.style.display = 'block';
            
            // Mostra anteprima
            const previewSection = document.getElementById('previewSection');
            const previewContent = document.getElementById('previewContent');
            let previewLines = [];
            
            previewLines.push('╔════════════════════════════════════════════════════════════════════════════════╗');
            previewLines.push('║                              CONTENUTO COMPLETO DEL FILE                         ║');
            previewLines.push('╚════════════════════════════════════════════════════════════════════════════════╝');
            previewLines.push('');
            
            lines.forEach((line, idx) => {
                if (line.substring(0,3) === 'RMA') {
                    previewLines.push(`[${idx+1}] RMA | ProgRecord:${line.substring(3,10)} | ID File:${line.substring(10,30).trim()} | Data:${line.substring(30,38)}`);
                } else if (line.substring(0,3) === 'RMD') {
                    const progRecord = line.substring(3,10);
                    const progRich = line.substring(10,17);
                    const cf = line.substring(17,33).trim();
                    const impRaw = line.substring(49,64);
                    const impEuro = (parseInt(impRaw) / 100).toFixed(2);
                    previewLines.push(`[${idx+1}] RMD | ProgRecord:${progRecord} | ProgRich:${progRich} | CF:"${cf}" | Importo:€ ${impEuro}`);
                } else if (line.substring(0,3) === 'RMZ') {
                    const totalRec = line.substring(38,45);
                    previewLines.push(`[${idx+1}] RMZ | ProgRecord:${line.substring(3,10)} | Totale Record:${totalRec}`);
                }
            });
            
            previewContent.textContent = previewLines.join('\n');
            previewSection.style.display = 'block';
        }

        // Download file
        function downloadFile() {
            if (!generatedContent) {
                generateAndPreview();
            }
            
            if (!generatedContent) {
                return;
            }
            
            const filename = document.getElementById('filename').value.trim();
            const blob = new Blob([generatedContent], { type: 'text/plain;charset=windows-1252' });
            const link = document.createElement('a');
            const url = URL.createObjectURL(blob);
            link.href = url;
            link.download = filename;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            URL.revokeObjectURL(url);
            
            const lines = generatedContent.split('\n');
            showMessage(`✅ File "${filename}" scaricato con successo! Totale record: ${lines.length}`);
        }

        // Reset form
        function resetForm() {
            document.getElementById('filename').value = 'IRMEQS20250000000001.TXT';
            const now = new Date();
            const creationDate = now.getFullYear() + 
                                String(now.getMonth() + 1).padStart(2, '0') + 
                                String(now.getDate()).padStart(2, '0');
            document.getElementById('creationDate').value = creationDate;
            document.getElementById('previewSection').style.display = 'none';
            document.getElementById('statsSection').style.display = 'none';
            document.getElementById('detailSection').style.display = 'none';
            document.getElementById('downloadBtn').disabled = true;
            document.getElementById('successMessage').style.display = 'none';
            document.getElementById('errorMessage').style.display = 'none';
            generatedContent = null;
            generatedRecords = [];
            validateFilename();
            
            // Resetta anche i dati dei fornitori
            suppliersData = [];
            renderSupplierTable();
        }

        // Inizializza
        renderSupplierTable();
        const now = new Date();
        document.getElementById('creationDate').value = now.getFullYear() + 
                                                       String(now.getMonth() + 1).padStart(2, '0') + 
                                                       String(now.getDate()).padStart(2, '0');
        validateFilename();
    </script>
</body>
</html>