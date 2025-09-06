<!-- ...existing code... -->

<style>
  body {
    font-family: 'Segoe UI', Arial, sans-serif;
    background: #f4f6fa;
    margin: 0;
    padding: 30px;
  }
  h2, h3 {
    color: #2d3a4a;
  }
  form {
    background: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.07);
    margin-bottom: 30px;
    display: flex;
    gap: 10px;
    align-items: center;
  }
  input[type="file"], input[type="date"] {
    padding: 6px;
    border-radius: 4px;
    border: 1px solid #d1d5db;
  }
  button {
    background: #2563eb;
    color: #fff;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: 500;
    transition: background 0.2s;
  }
  button:hover {
    background: #1e40af;
  }
  ul#fileList {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  ul#fileList li {
    background: #fff;
    margin-bottom: 10px;
    padding: 14px 18px;
    border-radius: 6px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.05);
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
  }
  .file-info {
    flex: 1;
  }
  .file-actions button {
    margin-left: 8px;
    background: #e5e7eb;
    color: #2d3a4a;
    border: none;
    padding: 6px 12px;
    border-radius: 4px;
    cursor: pointer;
    transition: background 0.2s;
  }
  .file-actions button:hover {
    background: #d1d5db;
  }
  /* Modal styles */
  #pdfModal {
    display: none;
    position: fixed;
    z-index: 9999;
    left: 0; top: 0;
    width: 100vw; height: 100vh;
    background: rgba(0,0,0,0.6);
    align-items: center;
    justify-content: center;
  }
  #pdfModal.active {
    display: flex;
  }
  #pdfViewer {
    background: #fff;
    border-radius: 8px;
    padding: 20px;
    max-width: 80vw;
    max-height: 80vh;
    box-shadow: 0 2px 16px rgba(0,0,0,0.15);
    display: flex;
    flex-direction: column;
    align-items: flex-end;
  }
  #pdfViewer embed {
    width: 70vw;
    height: 70vh;
    border-radius: 6px;
    border: 1px solid #d1d5db;
  }
  #closeModal {
    background: #ef4444;
    color: #fff;
    border: none;
    padding: 6px 14px;
    border-radius: 4px;
    cursor: pointer;
    margin-bottom: 10px;
    font-weight: 500;
  }
  #closeModal:hover {
    background: #b91c1c;
  }
</style>

<h2>Subir roles de turno (PDF)</h2>
<form id="uploadForm">
  <input type="file" id="fileInput" accept=".pdf" required />
  <input type="date" id="dateInput" required />
  <button type="submit">Subir archivo</button>
</form>

<h3>Archivos subidos</h3>
<input type="text" id="searchInput" placeholder="Buscar archivo PDF..." style="width: 100%; max-width: 400px; margin-bottom: 18px; padding: 8px; border-radius: 4px; border: 1px solid #d1d5db;">
<ul id="fileList"></ul>

<!-- Modal para visor PDF -->
<div id="pdfModal">
  <div id="pdfViewer">
    <button id="closeModal">Cerrar</button>
    <embed id="pdfEmbed" src="" type="application/pdf" />
  </div>
</div>

<script>
  // Array para almacenar archivos y fechas
  const files = [];

  document.getElementById('uploadForm').addEventListener('submit', function(e) {
    e.preventDefault();
    const fileInput = document.getElementById('fileInput');
    const dateInput = document.getElementById('dateInput');
    const file = fileInput.files[0];
    const date = dateInput.value;

    if (file && date) {
      // Guardar el archivo como objeto URL para vista previa
      files.push({ name: file.name, date: date, file: file, url: URL.createObjectURL(file) });
      files.sort((a, b) => new Date(a.date) - new Date(b.date));
      renderFileList();
      fileInput.value = '';
      dateInput.value = '';
    }
  });

  function renderFileList() {
    const list = document.getElementById('fileList');
    list.innerHTML = '';
    files.forEach((f, idx) => {
      const li = document.createElement('li');
      const info = document.createElement('span');
      info.className = 'file-info';
      info.textContent = `${f.name} - ${f.date}`;

      const actions = document.createElement('span');
      actions.className = 'file-actions';

      // Botón Ver
      const viewBtn = document.createElement('button');
      viewBtn.textContent = 'Ver';
      viewBtn.onclick = () => showPDF(f.url);

      // Botón Quitar
      const removeBtn = document.createElement('button');
      removeBtn.textContent = 'Quitar';
      removeBtn.onclick = () => {
        // Liberar el objeto URL
        URL.revokeObjectURL(f.url);
        files.splice(idx, 1);
        renderFileList();
      };

      actions.appendChild(viewBtn);
      actions.appendChild(removeBtn);

      li.appendChild(info);
      li.appendChild(actions);
      list.appendChild(li);
    });
  }

  // Modal PDF
  const pdfModal = document.getElementById('pdfModal');
  const pdfEmbed = document.getElementById('pdfEmbed');
  const closeModal = document.getElementById('closeModal');

  function showPDF(url) {
    pdfEmbed.src = url;
    pdfModal.classList.add('active');
  }

  closeModal.onclick = () => {
    pdfModal.classList.remove('active');
    pdfEmbed.src = '';
  };

  // Cerrar modal al hacer click fuera del visor
  pdfModal.onclick = (e) => {
    if (e.target === pdfModal) {
      pdfModal.classList.remove('active');
      pdfEmbed.src = '';
    }
  };
</script>

<!-- ...existing code... -->
