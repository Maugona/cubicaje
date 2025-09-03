<!DOCTYPE html>
<html lang="es">
<head>
 <script src="https://unpkg.com/pdfjs-dist@4.0.379/build/pdf.min.js"></script>
<script>
  if (typeof window.pdfjsLib === 'undefined' && typeof window.pdfjsDistBuildPdf !== 'undefined') {
    window.pdfjsLib = window.pdfjsDistBuildPdf;
  }
</script>
<script src="https://cdn.jsdelivr.net/npm/tesseract.js@5/dist/tesseract.min.js"></script>
  <!-- ...el resto de tu head... -->
</head>
<title>Sistema de cubicaje - Comercializadora de Llantas Tres Siglos</title>
<link rel="icon" type="image/png" href="https://http2.mlstatic.com/storage/mshops-appearance-api/images/13/1184895213/logo-2022082314215812800.png">
<style>
    /* ... tu CSS existente sin cambios ... */
    body {
        font-family: Arial, sans-serif;
        margin: 0; padding: 0;
        background: url('https://www.firestone.com.mx/content/dam/consumer/fst/la/mx/tips/comprar-llantas/Llantas_Nuevas_big.jpg') no-repeat center fixed;
        background-size: cover;
    }                   
    header {
        display: flex;
        align-items: center;
        background: #b0dab9bb;
        color: #24412b;
        padding: 12px 24px;
    }
    header img {
        height: 44px;
        margin-right: 12px;
        opacity: 0.7;
    }
    nav {
        display: flex;
        background: #b0dab9e6;
    }
    nav button {
        flex: 1;
        padding: 12px 0;
        color: #24412b;
        background: transparent;
        border: none;
        cursor: pointer;
        font-weight: bold;
        letter-spacing: 1px;
        transition: background 0.3s;
    }
    nav button:hover, nav button.active {
        background: #d9efe0;
    }
    section {
        background: rgba(255,255,255,0.88);
        border-radius: 16px;
        margin: 32px auto 16px auto;
        max-width: 1200px;
        box-shadow: 0 8px 32px rgba(72,144,81,0.13);
        padding: 28px 22px;
    }
    .tabcontent {
        display: none;
        background: transparent;
    }
    .tabcontent.active {
        display: block;
    }
    table {
        width: 100%;
        border-collapse: collapse;
        margin-top: 12px;
        background: white;
        border-radius: 8px;
        overflow: hidden;
    }
    th, td {
        border: 1px solid #e2e2e2;
        padding: 8px 12px;
        text-align: center;
    }
    th {
        background: #f7fcf8;
    }
    .search-bar {
        margin-top: 8px;
        margin-bottom: 12px;
        padding: 7px;
        font-size: 17px;
        border-radius: 5px;
        border: 1px solid #cde5d4;
        flex-grow: 1;
    }
    button.primary {
        background: #489051;
        color: white;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        padding: 8px 18px;
        font-weight: bold;
        margin-top: 0;
        transition: background 0.3s;
        white-space: nowrap;
    }
    button.primary:hover {
        background: #75c286;
    }
    .highlight-yellow {
        background-color: #fffa8b;
        transition: background-color 1s;
    }
    .graph-container {
        width: 30%;
        background: #f5fdf7;
        padding: 16px;
        border-radius: 14px;
        border: 1px solid #e2e2e2;
        margin: 8px 5px 16px 0;
        display: inline-block;
        vertical-align: top;
        box-shadow: 0 3px 12px #d6eedd83;
    }
    @media (max-width: 900px){
        .graph-container{ width: 95%; margin:auto; margin-bottom:16px;}
    }
    .search-and-button {
        display: flex;
        align-items: center;
        gap: 12px;
        margin-bottom: 12px;
        max-width: 700px;
        flex-wrap: wrap;
    }

    /* Modal base styles */
    .modal {
        display: none; 
        position: fixed; 
        z-index: 1000;
        left: 0; top: 0;
        width: 100%; height: 100%;
        overflow: auto;
        background-color: rgba(0,0,0,0.4); /* fondo semitransparente */
    }
    .modal-content {
        background-color: #fefefe;
        margin: 5% auto; /* centrado vertical */
        padding: 20px;
        border-radius: 12px;
        width: 90%;
        max-width: 600px;
        position: relative;
        box-shadow: 0 6px 20px rgba(0,0,0,0.3);
    }
    .close {
        position: absolute;
        right: 20px;
        top: 10px;
        font-size: 28px;
        font-weight: bold;
        cursor: pointer;
        color: #555;
        user-select: none;
    }

    form.add-form label {
        display: block;
        margin: 12px 0 5px 0;
        font-weight: bold;
        color: #35672b;
    }
    form.add-form input[type=text], form.add-form input[type=number] {
        width: 100%;
        padding: 8px 10px;
        border: 1px solid #a3d087;
        border-radius: 6px;
        box-sizing: border-box;
        margin-bottom: 12px;
        font-size: 16px;
        color: #24412b;
    }
    form.add-form button.submit-btn {
        margin-top: 10px;
        padding: 10px 20px;
        background: #489051;
        color: white;
        border: none;
        font-weight: bold;
        border-radius: 6px;
        cursor: pointer;
        transition: background 0.3s;
        width: 100%;
        font-size: 17px;
    }
    form.add-form button.submit-btn:hover {
        background: #75c286;
    }
    .msg {
        margin: 8px 0 0 0;
        font-size: 15px;
        min-height: 20px;
    }
    .msg.success {
        color: green;
    } 
    .msg.error {
        color: red;
    }
</style>
</head>
<body>

<header>
    <img src="https://cdn.prod.website-files.com/62b4e3084bb69b3cbd747e80/62b4e344650db7626d857053_TS_ORGINAL_LOGO.png" alt="Logo Tres Siglos" />
    <h1>Sistema de cubicaje - Comercializadora de Llantas Tres Siglos</h1>
</header>

<nav>
    <button class="tablink active" data-tab="inventario">Inventario</button>
    <button class="tablink" data-tab="flota">Flota</button>
    <button class="tablink" data-tab="facturas">Facturas</button>
    <button class="tablink" data-tab="pedidos">Pedidos</button>
    <button class="tablink" data-tab="pedidos-confirmados">Pedidos Confirmados</button>
</nav>

<section>

    <!-- Inventario -->
    <div id="inventario" class="tabcontent active">
        <div class="search-and-button">
            <input type="text" id="searchInventario" class="search-bar" placeholder="Buscar por ID Llanta..." oninput="searchInventario()" />
            <button class="primary" onclick="openModal('modalInventario')">Agregar Llanta</button>
            <button class="primary" onclick="fetchInventario()">Actualizar inventario</button>
        </div>

        <table id="tablaInventario">
            <thead>
                <tr>
                    <th>clave</th>
                    <th>Descripción</th>
                    <th>Línea</th>
                    <th>Peso (kg)</th>
                    <th>Volumen (m³)</th>
                    <th>Valor ($)</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>

    <!-- Modal Inventario -->
    <div id="modalInventario" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('modalInventario')">&times;</span>
            <form id="formAgregarLlanta" class="add-form" onsubmit="event.preventDefault(); agregarNuevaLlanta();">
                <h3>Agregar Nueva Llanta</h3>
                <label for="agregarId">ID (dejar vacío para autogenerar)</label>
                <input type="text" id="agregarId" placeholder="Ejemplo: 1001 o dejar vacío para auto" />

                <label for="agregarDescripcion">Descripción</label>
                <input type="text" id="agregarDescripcion" placeholder="Descripción de la llanta" required />

                <label for="agregarPeso">Peso (kg)</label>
                <input type="number" id="agregarPeso" step="0.01" min="0" placeholder="Ejemplo: 12.5" required />

                <label for="agregarVolumen">Volumen unitario (m³)</label>
                <input type="number" id="agregarVolumen" step="0.0001" min="0" placeholder="Ejemplo: 0.0035" required />

                <label for="agregarValor">Valor unitario ($)</label>
                <input type="number" id="agregarValor" step="0.01" min="0" placeholder="Ejemplo: 1500.00" required />

                <button type="submit" class="submit-btn">Agregar Llanta</button>
                <div id="msgInventario" class="msg"></div>

                <label for="agregarLínea">Línea</label>
                <input type="text" id="agregarLínea" placeholder="Ejemplo: Industrial" required />
            </form>
        </div>
    </div>

    <!-- Flota -->
    <div id="flota" class="tabcontent">
        <div class="search-and-button">
            <input type="text" id="searchFlota" class="search-bar" placeholder="Buscar por Número Económico..." oninput="searchFlota()" />
            <button class="primary" onclick="openModal('modalFlota')">Agregar Camión</button>
            <button class="primary" onclick="fetchFlota()">Actualizar flota</button>
        </div>

        <table id="tablaFlota">
            <thead>
                <tr>
                    <th>Económico</th>
                    <th>Unidad</th>
                    <th>Asignado</th>
                    <th>Modelo</th>
                    <th>identificacion</th>
                    <th>Ubicación</th>
                    <th>capacidad de carga (kg)</th>
                    <th>Volumen (m³)</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>

    <!-- Modal Flota -->
    <div id="modalFlota" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('modalFlota')">&times;</span>
            <form id="formAgregarCamion" class="add-form" onsubmit="event.preventDefault(); agregarNuevoCamion();">
                <h3>Agregar Nuevo Camión</h3>

                <label for="agregarEconomico">Número Económico (dejar vacío para autogenerar)</label>
                <input type="text" id="agregarEconomico" placeholder="Ejemplo: 101 o dejar vacío para auto" />

                <label for="agregarUnidad">Unidad</label>
                <input type="text" id="agregarUnidad" placeholder="Unidad/vehículo" required />

                <label for="agregarAsignado">Asignado</label>
                <input type="text" id="agregarAsignado" placeholder="Nombre responsable" required />

                <label for="agregarModelo">Modelo</label>
                <input type="text" id="agregarModelo" placeholder="Modelo del camión" required />

                <label for="agregarPlacas">Placas</label>
                <input type="text" id="agregarPlacas" placeholder="Placas del camión" required />

                <label for="agregarUbicacion">Ubicación</label>
                <input type="text" id="agregarUbicacion" placeholder="Ubicación del camión" required />

                <label for="agregarCarga">Capacidad de Carga (kg)</label>
                <input type="number" id="agregarCarga" step="0.01" min="0" placeholder="Ejemplo: 15000" required />

                <label for="agregarVolumenCamion">Capacidad de Volumen (m³)</label>
                <input type="number" id="agregarVolumenCamion" step="0.0001" min="0" placeholder="Ejemplo: 40.5" required />

                <button type="submit" class="submit-btn">Agregar Camión</button>
                <div id="msgFlota" class="msg"></div>
            </form>      
        </div>
    </div>
          
    <!-- Pedidos -->    
    <div id="pedidos" class="tabcontent" style="max-width: 1000px;">
        <div>
            <label for="inputPedidoNumEconomico">Número Económico Camión:</label>
            <input type="text" id="inputPedidoNumEconomico" oninput="llenarDatosCamionPedido()" placeholder="Ingrese número económico" />
        </div>                
        <div id="datosCamionPedido" style="margin-top:10px; font-weight:bold; min-height: 50px;"></div>
          
        <div style="margin-top: 20px;">
            <div class="graph-container">
                <canvas id="graphVolumen" width="150" height="50"></canvas>
                <p style="text-align:center">Volumen Usado</p>
            </div>
            <div class="graph-container">
                <canvas id="graphCarga" width="150" height="50"></canvas>
                <p style="text-align:center">Carga Usada</p>
            </div>
        </div>

        <h3>Agregar Llanta al Pedido</h3>
        <table id="tablaPedidoAgregar" style="max-width:700px;">
            <thead>
                <tr>
                    <th>Código Llanta</th>
                    <th>Descripción</th>
                    <th>Línea</th>
                    <th>Cantidad</th>
                    <th>Peso</th>
                    <th>Volumen</th>
                    <th>Valor Unitario ($)</th>
                    <th>Acción</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                   <td><input type="text" id="pedidoCodigoLlanta" oninput="autoCompletarLlantaPedidoPorCodigo()" /></td>
                   <td><input type="text" id="pedidoDescripcionLlantaInput" oninput="autoCompletarLlantaPedidoPorDescripcion()" /></td>
                   <td id="pedidoLineaLlanta"></td>
                   <td><input type="number" id="pedidoCantidadLlanta" value="1" min="1" oninput="calcularTotalesPedido()" /></td>
                   <td id="pedidoPesoLlanta">0</td>
                   <td id="pedidoVolumenLlanta">0</td>
                   <td id="pedidoValorUnitarioLlanta">0</td>
                   <td><button class="primary" onclick="agregarPedido()">Agregar</button></td>
               </tr>
            </tbody>
        </table>

       <label>Buscar lote de facturas: 
         <input id="buscarLoteFacturas" placeholder="Escribe el código del lote" oninput="cargarPedidosDesdeFacturas()" />
       </label>

       <h3>Pedidos actuales del camión</h3>
       <table id="tablaPedidosActuales" style="max-width:700px;">
           <thead>
               <tr>
                  <th>Código</th>
                  <th>Descripción</th>
                  <th>Línea</th>
                  <th>Cantidad</th>
                  <th>Volumen Total</th>
                  <th>Peso Total</th>
                  <th>Valor Total ($)</th>
                  <th>Quitar</th>
               </tr>
           </thead>
           <tbody></tbody>
        </table>

        <div style="margin-top: 10px; font-weight: bold;">
            <span id="totalesPedido"></span>
        </div>

        <button class="primary" onclick="aceptarPedido()" style="margin-top: 10px;">Aceptar Pedido</button>
    </div>

    <!-- Pedidos Confirmados -->
    <div id="pedidos-confirmados" class="tabcontent" style="max-width: 1200px;">
        <h3>Pedidos Confirmados</h3>
        <table id="tabla">
            <thead>
                <tr>
                    <th>Camión</th>
                    <th>Llantas</th>
                    <th>Descripción</th>
                    <th>Cantidad</th>
                    <th>Total,Cantidad</th>
                    <th>Línea</th>
                    <th>Volumen</th>
                    <th>Peso</th>
                    <th>Valor ($)</th>
                    <th>Fecha</th>
                    <th>Acción</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    <!-- Sección de Escaneo de Facturas -->
    <div id="facturas" class="tabcontent" style="max-width: 1200px;">
    <h3>Escaneo y carga de facturas PDF</h3>
    <input type="file" id="inputFacturasPDF" multiple accept="application/pdf" />
    <button class="primary" onclick="procesarFacturasPDF()">Procesar PDFs</button>
    <table id="tablaFacturas" style="margin-top:18px;">
        <thead>
            <tr>
                <th>Folio</th>
                <th>Fecha de Emisión</th>
                <th>Usuario</th>
                <th>Cantidad</th>
                <th>Código</th>
                <th>Descripción</th>
                <th>Fecha de Subida</th>
            </tr>
        </thead>
        <tbody></tbody>
    </table>
    <label>Nombre/Código del lote de facturas: <input id="nombreLoteFacturas" placeholder="Ejemplo: PEDIDO_2025_09_02" /></label>
    <button class="primary" onclick="guardarFacturas()">Guardar Facturas</button>
    <button class="primary" onclick="guardarFacturas()">Guardar Facturas</button>
</div>
  
</section>
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
    // Variables de datos
    let inventario = [];
    let flota = [];
    let pedidosConfirmados = [];
    let pedidosEnCurso = [];
    let pedidoCamion = null;

    // --- NUEVO: Cargar pedidos desde facturas por lote ---
    async function cargarPedidosDesdeFacturas() {
        const lote = document.getElementById('buscarLoteFacturas').value.trim();
        if (!lote) return;
        try {
            const res = await fetch(`https://sheetdb.io/api/v1/lttpt3mvohen7/search?sheet=facturas&lote=${lote}`);
            if (!res.ok) throw new Error('No se pudo cargar el lote');
            const facturas = await res.json();
            // Limpia pedidosEnCurso y llena con los datos de las facturas
            pedidosEnCurso = [];
            facturas.forEach(factura => {
                // Busca la llanta en inventario para obtener peso, volumen y valor
                const llanta = inventario.find(item => item.clave == factura.codigo);
                pedidosEnCurso.push({
                    clave: factura.codigo,
                    descripcion: factura.descripcion,
                    linea: llanta ? llanta.linea || '' : '',
                    cantidad: Number(factura.cantidad),
                    peso: llanta ? (+llanta.peso) * Number(factura.cantidad) : 0,
                    volumen: llanta ? (+llanta.volumen) * Number(factura.cantidad) : 0,
                    valor: llanta ? (+llanta.valor) * Number(factura.cantidad) : 0
                 });
             });
             renderPedidosActuales();
             actualizarGraficas();
         } catch (e) {
             alert('Error al cargar el lote: ' + e.message);
         }
     }

// Abrir y cerrar modales
function openModal(id) {
    document.getElementById(id).style.display = 'block';
}
function closeModal(id) {
    document.getElementById(id).style.display = 'none';
}
// Cerrar modal si el usuario hace click fuera del contenido
window.onclick = function(event) {
    const modales = ['modalInventario','modalFlota'];
    modales.forEach(id => {
        const modal = document.getElementById(id);
        if(event.target === modal) {
            modal.style.display = 'none';
        }
    });
};
    // ---------- Funciones para cargar datos ---------
    async function fetchInventario() {
        try {
            const res = await fetch('https://sheetdb.io/api/v1/lttpt3mvohen7');
            if (!res.ok) throw new Error('Error al cargar inventario');
            inventario = await res.json();
            renderInventario();
        } catch (e) {
            alert('No se pudo cargar el inventario: ' + e.message);
        }
    }
    async function fetchFlota() {
        try {
            const res = await fetch('https://sheetdb.io/api/v1/lttpt3mvohen7?sheet=flota');
            if (!res.ok) throw new Error('Error al cargar flota');
            flota = await res.json();
            renderFlota();
        } catch (e) {
            alert('No se pudo cargar la flota: ' + e.message);
        }
    }
    fetchInventario();
    fetchFlota();

    // Función para cargar pedidos confirmados desde hoja
    async function fetchPedidosConfirmados() {
        try {
            const res = await fetch('https://sheetdb.io/api/v1/lttpt3mvohen7?sheet=confirmados');
            if (!res.ok) throw new Error('Error al cargar pedidos confirmados');
            pedidosConfirmados = await res.json();
            renderPedidosConfirmados();
        } catch (e) {
            alert('No se pudieron cargar los pedidos confirmados: ' + e.message);
        }
    }

    // ----- Cambiar pestañas -----
    const tablinks = document.querySelectorAll('.tablink');
    const tabcontents = document.querySelectorAll('.tabcontent');
    tablinks.forEach(button => {
        button.addEventListener('click', () => {
            tablinks.forEach(btn => btn.classList.remove('active'));
            tabcontents.forEach(tc => tc.classList.remove('active'));
            button.classList.add('active');
            document.getElementById(button.dataset.tab).classList.add('active');
            if (button.dataset.tab === 'inventario') renderInventario();
            if (button.dataset.tab === 'flota') renderFlota();
            if (button.dataset.tab === 'pedidos') resetPedidoInputs();
            if (button.dataset.tab === 'pedidos-confirmados') fetchPedidosConfirmados();
        });
    });

    // ---------- Renderizar Inventario ----------
    function renderInventario() {
    const tbody = document.querySelector('#tablaInventario tbody');
    tbody.innerHTML = '';
    inventario.forEach(llanta => {
        const tr = document.createElement('tr');
        tr.innerHTML = `
            <td>${llanta.clave}</td>
            <td>${llanta.descripcion}</td>
            <td>${llanta.linea || ''}</td>
            <td>${(+llanta.peso).toFixed(3)}</td>
            <td>${(+llanta.volumen).toFixed(3)}</td>
            <td>$${(+llanta.valor).toFixed(3)}</td>
            <td>
            <button onclick="editarLlanta('${llanta.clave}')">Editar</button>
            <button onclick="eliminarLlanta('${llanta.clave}')">Eliminar</button>
            </td>
        `;
        tbody.appendChild(tr);
    });
    highlightSearch('inventario', document.getElementById('searchInventario').value);
   }
   async function eliminarLlanta(clave) {
     if (!confirm('¿Seguro que deseas eliminar esta llanta?')) return;
     try {
       const res = await fetch(`https://sheetdb.io/api/v1/cz5zxp3959aew/clave/${clave}`, {
         method: 'DELETE'
      });
      if (!res.ok) throw new Error('No se pudo eliminar');
      inventario = inventario.filter(item => item.clave !== clave);
      renderInventario();
      alert('Llanta eliminada correctamente.');
    } catch (error) {
      alert('Error al eliminar: ' + error.message);
    }
  }
  function editarLlanta(clave) {
  const llanta = inventario.find(item => item.clave === clave);
  // Muestra el modal con los datos actuales
  document.getElementById('modalInventario').innerHTML = `
    <div class="modal-content">
      <h3>Editar Llanta</h3>
      <label>Descripción: <input id="editDescripcion" value="${llanta.descripcion}" /></label><br>
      <label>Línea: <input id="editLinea" value="${llanta.linea}" /></label><br>
      <label>Peso: <input id="editPeso" type="number" step="0.0001" value="${llanta.peso}" /></label><br>
      <label>Volumen: <input id="editVolumen" type="number" step="0.0001" value="${llanta.volumen}" /></label><br>
      <label>Valor: <input id="editValor" type="number" step="0.0001" value="${llanta.valor}" /></label><br>
      <button onclick="guardarEdicionLlanta('${llanta.clave}')">Guardar</button>
      <button onclick="closeModal('modalInventario')">Cancelar</button>
    </div>
  `;
  openModal('modalInventario');
}

async function guardarEdicionLlanta(clave) {
  const nuevosDatos = {
    descripcion: document.getElementById('editDescripcion').value,
    linea: document.getElementById('editLinea').value,
    peso: document.getElementById('editPeso').value,
    volumen: document.getElementById('editVolumen').value,
    valor: document.getElementById('editValor').value
  };
  try {
    const res = await fetch(`https://sheetdb.io/api/v1/lttpt3mvohen7/clave/${clave}`, {
      method: 'PATCH',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ data: nuevosDatos })
    });
    if (!res.ok) throw new Error('No se pudo editar');
    // Actualiza localmente y vuelve a renderizar
    const llanta = inventario.find(item => item.clave === clave);
    Object.assign(llanta, nuevosDatos);
    renderInventario();
    closeModal('modalInventario');
    alert('Llanta editada correctamente.');
  } catch (error) {
    alert('Error al editar: ' + error.message);
  }
}

// Buscar ID inventario
function searchInventario() {
    const filter = document.getElementById('searchInventario').value.toLowerCase();
    const tbody = document.querySelector('#tablaInventario tbody');
     for (let row of tbody.rows) {
        const claveCell = row.cells[0].textContent.toLowerCase();
        const descripcionCell = row.cells[1].textContent.toLowerCase();
        // Busca en clave o descripción
        const match = claveCell.includes(filter) || descripcionCell.includes(filter);
        row.style.display = match ? '' : 'none';
        if (match && filter) {
            row.classList.add('highlight-yellow');
                setTimeout(() => row.classList.remove('highlight-yellow'), 1100);
            }
        }
    }
    function highlightSearch(tab, valor) {
        if (!valor) return;
        let rows = document.querySelector(`#tabla${tab.charAt(0).toUpperCase() + tab.slice(1)} tbody`).rows;
        [...rows].forEach(row => {
            if (row.cells[0].textContent.toLowerCase().includes(valor.toLowerCase())) {
                row.classList.add('highlight-yellow');
                row.scrollIntoView({ behavior: "smooth", block: "center" });
                setTimeout(() => row.classList.remove('highlight-yellow'), 900);
            }
        });
    }
    function buscarLlantaPorId(id) {
        return inventario.find(llanta => llanta.id === id);
    }

    // ---------- Agregar nueva llanta a SheetDB ----------
    async function agregarNuevaLlanta() {
        const idInput = document.getElementById('agregarId').value.trim();
        const descripcion = document.getElementById('agregarDescripcion').value.trim();
        const peso = parseFloat(document.getElementById('agregarPeso').value);
        const volumen = parseFloat(document.getElementById('agregarVolumen').value);
        const valor = parseFloat(document.getElementById('agregarValor').value);
        const Línea = document.getElementById('agregarLínea').value.trim();
        const msgDiv = document.getElementById('msgInventario');
        msgDiv.textContent = '';
        msgDiv.className = 'msg';

        if (!descripcion || isNaN(peso) || isNaN(volumen) || isNaN(valor) || !Línea) {
            msgDiv.textContent = 'Por favor completa todos los campos correctamente.';
            msgDiv.classList.add('error');
            return;
        }

        let id = idInput || generarNuevoIdInventario();

        if (inventario.some(ll => ll.id === id)) {
            msgDiv.textContent = 'El ID ya existe. Por favor usa otro.';
            msgDiv.classList.add('error');
            return;
        }

        const nuevoDato = { id, descripcion, peso, volumen, valor, "Línea": Línea };

        try {
            const res = await fetch('https://sheetdb.io/api/v1/lttpt3mvohen7', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ data: nuevoDato })
            });
            if (!res.ok) throw new Error('Error al agregar llanta');
            msgDiv.textContent = 'Llanta agregada correctamente!';
            msgDiv.classList.add('success');
            limpiarFormularioInventario();
            await fetchInventario();
            closeModal('modalInventario');
        } catch (e) {
            msgDiv.textContent = 'Error: ' + e.message;
            msgDiv.classList.add('error');
        }
    }
    function generarNuevoIdInventario() {
        if (!inventario.length) return "1";
        let maxId = inventario.reduce((max, ll) => {
            let n = parseInt(ll.id);
            return n > max ? n : max;
        }, 0);
        return String(maxId + 1);
    }
    function limpiarFormularioInventario() {
        document.getElementById('agregarId').value = '';
        document.getElementById('agregarDescripcion').value = '';
        document.getElementById('agregarPeso').value = '';
        document.getElementById('agregarVolumen').value = '';
        document.getElementById('agregarValor').value = '';
    }

    // ---------- Renderizar Flota ----------
  function renderFlota() {
    const tbody = document.querySelector('#tablaFlota tbody');
    tbody.innerHTML = '';
    flota.forEach(camion => {
        const cargaNum = parseFloat(camion["capacidad de carga (kg)"]);
        const volumenNum = parseFloat(camion["volumen"]);
        const cargaMostrar = isNaN(cargaNum) ? '-' : cargaNum.toFixed(3);
        const volumenMostrar = isNaN(volumenNum) ? '-' : volumenNum.toFixed(3);
        const tr = document.createElement('tr');
        tr.innerHTML = `
            <td>${camion.economico || '-'}</td>
            <td>${camion.unidad || '-'}</td>
            <td>${camion.asignado || camion.encargado || '-'}</td>
            <td>${camion.modelo || '-'}</td>
            <td>${camion.identificacion || '-'}</td>
            <td>${camion.ubicacion || '-'}</td>
            <td>${cargaMostrar}</td>
            <td>${volumenMostrar}</td>
            <td>
            <button onclick="editarCamion('${camion.economico}')">Editar</button>
            <button onclick="eliminarCamion('${camion.economico}')">Eliminar</button>
            </td>
         `;
        tbody.appendChild(tr);
    });
    highlightSearch('flota', document.getElementById('searchFlota').value);
}
     async function eliminarCamion(economico) {
       if (!confirm('¿Seguro que deseas eliminar este camión?')) return;
       try {
         const res = await fetch(`https://sheetdb.io/api/v1/lttpt3mvohen7/economico/${economico}?sheet=flota`, {
           method: 'DELETE'
         });
         if (!res.ok) throw new Error('No se pudo eliminar');
         flota = flota.filter(item => item.economico !== economico);
         renderFlota();
         alert('Camión eliminado correctamente.');
       } catch (error) {
         alert('Error al eliminar: ' + error.message);
       }
     } 
    function editarCamion(economico) {
        const camion = flota.find(item => item.economico === economico);
        document.getElementById('modalFlota').innerHTML = `
          <div class="modal-content">
            <h3>Editar Camión</h3>
            <label>Número Económico: <input id="editCamionEconomico" value="${camion.economico}" readonly /></label><br>
            <label>Nombre (Unidad): <input id="editCamionUnidad" value="${camion.unidad || ''}" /></label><br>
            <label>Capacidad de carga (kg): <input id="editCamionCarga" type="number" step="0.001" value="${camion['capacidad de carga (kg)'] || camion.carga || ''}" /></label><br>
            <label>Volumen (m³): <input id="editCamionVolumen" type="number" step="0.001" value="${camion.volumen || ''}" /></label><br>
            <button onclick="guardarEdicionCamion('${camion.economico}')">Guardar</button>
            <button onclick="closeModal('modalFlota')">Cancelar</button>
          </div>
        `;
        openModal('modalFlota');
    }

    async function guardarEdicionCamion(economico) {
      const nuevosDatos = {
        unidad: document.getElementById('editCamionUnidad').value,
        "capacidad de carga (kg)": document.getElementById('editCamionCarga').value,
        volumen: document.getElementById('editCamionVolumen').value
      };
      try {
        const res = await fetch(`https://sheetdb.io/api/v1/lttpt3mvohen7/economico/${economico}?sheet=flota`, {
          method: 'PATCH',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({ data: nuevosDatos })
        });
        if (!res.ok) throw new Error('No se pudo editar');
        const camion = flota.find(item => item.economico === economico);
        Object.assign(camion, nuevosDatos);
        renderFlota();
        closeModal('modalFlota');
        alert('Camión editado correctamente.');
      } catch (error) {          
        alert('Error al editar: ' + error.message);
      }
    }

    // ---------- Agregar nuevo camión a SheetDB ----------
    async function agregarNuevoCamion() {
        const economicoInput = document.getElementById('agregarEconomico').value.trim();
        const unidad = document.getElementById('agregarUnidad').value.trim();
        const asignado = document.getElementById('agregarAsignado').value.trim();
        const modelo = document.getElementById('agregarModelo').value.trim();
        const placas = document.getElementById('agregarPlacas').value.trim();
        const ubicacion = document.getElementById('agregarUbicacion').value.trim();
        const carga = parseFloat(document.getElementById('agregarCarga').value);
        const volumen = parseFloat(document.getElementById('agregarVolumenCamion').value);
        const msgDiv = document.getElementById('msgFlota');
        msgDiv.textContent = '';
        msgDiv.className = 'msg';

        if (!unidad || !asignado || !modelo || !placas || !ubicacion || isNaN(carga) || isNaN(volumen)) {
            msgDiv.textContent = 'Por favor completa todos los campos correctamente.';
            msgDiv.classList.add('error');
            return;
        }

        let economico = economicoInput || generarNuevoEconomico();

        if (flota.some(cam => cam.economico === economico)) {
            msgDiv.textContent = 'El número económico ya existe. Por favor usa otro.';
            msgDiv.classList.add('error');
            return;
        }

        const nuevoDato = {
            economico,
            unidad,
            asignado,
            modelo,
            placas,
            ubicacion,
            carga,
            volumen
        };

        try {
            const res = await fetch('https://sheetdb.io/api/v1/lttpt3mvohen7?sheet=flota', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ data: nuevoDato })
            });
            if (!res.ok) throw new Error('Error al agregar camión');
            msgDiv.textContent = 'Camión agregado correctamente!';
            msgDiv.classList.add('success');
            limpiarFormularioFlota();
            await fetchFlota();
            closeModal('modalFlota');
        } catch (e) {
            msgDiv.textContent = 'Error: ' + e.message;
            msgDiv.classList.add('error');
        }
    }
    function generarNuevoEconomico() {
        if (!flota.length) return "1";
        let maxEco = flota.reduce((max, cam) => {
            let n = parseInt(cam.economico);
            return n > max ? n : max;
        }, 0);
        return String(maxEco + 1);
    }
    function limpiarFormularioFlota() {
        document.getElementById('agregarEconomico').value = '';
        document.getElementById('agregarUnidad').value = '';
        document.getElementById('agregarAsignado').value = '';
        document.getElementById('agregarModelo').value = '';
        document.getElementById('agregarPlacas').value = '';
        document.getElementById('agregarUbicacion').value = '';
        document.getElementById('agregarCarga').value = '';
        document.getElementById('agregarVolumenCamion').value = '';
    }

    // ---------- Pedidos (igual que antes) ----------
    function llenarDatosCamionPedido() {
        const numEco = document.getElementById('inputPedidoNumEconomico').value.trim();
        const div = document.getElementById('datosCamionPedido');
        pedidoCamion = flota.find(c => c.economico.toString() === numEco);
        if (pedidoCamion) {
          const responsable = pedidoCamion.asignado || pedidoCamion.encargado || '-';
          div.innerText = `Camión: ${pedidoCamion.unidad}, Asignado: ${responsable}, Modelo: ${pedidoCamion.modelo}, Capacidad carga: ${pedidoCamion["capacidad de carga (kg)"] || '-'} kg, Cap. volumen: ${pedidoCamion["volumen"] || '-'} m³`;
            renderPedidosActuales();
            actualizarGraficas();
        } else {
            div.innerText = 'Camión no encontrado.';
            pedidosEnCurso = [];
            renderPedidosActuales();
            actualizarGraficas();
        }
    }
    function autoCompletarLlantaPedidoPorCodigo() {
        const codigo = document.getElementById('pedidoCodigoLlanta').value.trim();
        const llanta = inventario.find(item => item.clave.toString() === codigo);
        if (llanta) {
            document.getElementById('pedidoDescripcionLlantaInput').value = llanta.descripcion;
            document.getElementById('pedidoLineaLlanta').innerText = llanta.linea || '';
            document.getElementById('pedidoCantidadLlanta').value = 1;
            document.getElementById('pedidoPesoLlanta').innerText = Number(llanta.peso).toLocaleString('es-MX', {minimumFractionDigits: 2, maximumFractionDigits: 2});
            document.getElementById('pedidoVolumenLlanta').innerText = Number(llanta.volumen).toLocaleString('es-MX', {minimumFractionDigits: 3, maximumFractionDigits: 3});
            document.getElementById('pedidoValorUnitarioLlanta').innerText = Number(llanta.valor).toLocaleString('es-MX', {minimumFractionDigits: 2, maximumFractionDigits: 2}); 
        } else {
             document.getElementById('pedidoDescripcionLlantaInput').value = '';
             document.getElementById('pedidoLineaLlanta').innerText = '';
             document.getElementById('pedidoPesoLlanta').innerText = '0';
             document.getElementById('pedidoVolumenLlanta').innerText = '0';
             document.getElementById('pedidoValorUnitarioLlanta').innerText = '0';
        }
    }
    function autoCompletarLlantaPedidoPorDescripcion() {
        const descripcion = document.getElementById('pedidoDescripcionLlantaInput').value.trim().toLowerCase();
        const llanta = inventario.find(item => item.descripcion.toLowerCase() === descripcion);
        if (llanta) {
            document.getElementById('pedidoCodigoLlanta').value = llanta.clave;
            document.getElementById('pedidoLineaLlanta').innerText = llanta.linea || '';
            document.getElementById('pedidoCantidadLlanta').value = 1;
            document.getElementById('pedidoPesoLlanta').innerText = Number(llanta.peso).toLocaleString('es-MX', {minimumFractionDigits: 2, maximumFractionDigits: 2});
            document.getElementById('pedidoVolumenLlanta').innerText = Number(llanta.volumen).toLocaleString('es-MX', {minimumFractionDigits: 3, maximumFractionDigits: 3});
            document.getElementById('pedidoValorUnitarioLlanta').innerText = Number(llanta.valor).toLocaleString('es-MX', {minimumFractionDigits: 2, maximumFractionDigits: 2}); 
        } else {
             document.getElementById('pedidoDescripcionLlantaInput').value = '';
             document.getElementById('pedidoLineaLlanta').innerText = '';
             document.getElementById('pedidoPesoLlanta').innerText = '0';
             document.getElementById('pedidoVolumenLlanta').innerText = '0';
             document.getElementById('pedidoValorUnitarioLlanta').innerText = '0';
        }
    }
    function calcularTotalesPedido() {
        const cantidad = Number(document.getElementById('pedidoCantidadLlanta').value);
        const codigo = document.getElementById('pedidoCodigoLlanta').value.trim();
        const llanta = inventario.find(item => item.clave.toString() === codigo);
        if (llanta && cantidad > 0) {
            document.getElementById('pedidoPesoLlanta').innerText = Number(llanta.peso * cantidad).toLocaleString('es-MX', {minimumFractionDigits: 2, maximumFractionDigits: 2});
            document.getElementById('pedidoVolumenLlanta').innerText = Number(llanta.volumen * cantidad).toLocaleString('es-MX', {minimumFractionDigits: 4, maximumFractionDigits: 4});
            document.getElementById('pedidoValorUnitarioLlanta').innerText = Number(llanta.valor * cantidad).toLocaleString('es-MX', {minimumFractionDigits: 2, maximumFractionDigits: 2});
        }
    }
    function agregarPedido() {
        if (!pedidoCamion) {
            alert("Ingrese un número económico válido de camión primero.");
            return;
        }
        const codigo = document.getElementById('pedidoCodigoLlanta').value.trim();
        const cantidad = Number(document.getElementById('pedidoCantidadLlanta').value);
        if (cantidad <= 0) {
            alert("La cantidad debe ser mayor a 0.");
            return;
        }
        const llanta = inventario.find(item => item.clave.toString() === codigo);
        if (!llanta) {
            alert("Llanta no encontrada en inventario.");
            return;
        }
        const pedidoExistente = pedidosEnCurso.find(p => p.id === llanta.clave);
        if (pedidoExistente) {
            pedidoExistente.cantidad += cantidad;
            pedidoExistente.peso += (+llanta.peso * cantidad);
            pedidoExistente.volumen += (+llanta.volumen * cantidad);
            pedidoExistente.valor += (+llanta.valor * cantidad);
        } else {
            pedidosEnCurso.push({
                clave: llanta.clave,
                descripcion: llanta.descripcion,
                linea: llanta.linea || '',
                cantidad: cantidad,
                peso: (+llanta.peso) * cantidad,
                volumen: (+llanta.volumen) * cantidad,
                valor: (+llanta.valor) * cantidad
            });
        }
        renderPedidosActuales();
        actualizarGraficas();
        resetPedidoInputs();
    }                   
    function editarPedido(idx) {
        const pedido = pedidosEnCurso[idx];
        const nuevaCantidad = parseInt(prompt(`Editar cantidad para ${pedido.descripcion}:`, pedido.cantidad));
        if (isNaN(nuevaCantidad) || nuevaCantidad <= 0) return;

        // Actualiza los valores
        const llanta = inventario.find(item => item.clave.toString() === pedido.clave);
        pedido.cantidad = nuevaCantidad;
        pedido.peso = (+llanta.peso) * nuevaCantidad;
        pedido.volumen = (+llanta.volumen) * nuevaCantidad;
        pedido.valor = (+llanta.valor) * nuevaCantidad;

        renderPedidosActuales();
        actualizarGraficas();
    }
   function renderPedidosActuales() {
       const tbody = document.querySelector('#tablaPedidosActuales tbody');
       tbody.innerHTML = '';
       pedidosEnCurso.forEach((pedido, idx) => {
           const tr = document.createElement('tr');
           tr.innerHTML = `
               <td>${pedido.clave}</td>
               <td>${pedido.descripcion}</td>
               <td>${pedido.linea || ''}</td> 
               <td>${pedido.cantidad}</td>
               <td>${pedido.volumen.toFixed(3)}</td>
               <td>${pedido.peso.toFixed(3)}</td>
               <td>${pedido.valor.toLocaleString('es-MX', {minimumFractionDigits: 2, maximumFractionDigits: 2})}</td>
               <td>
                   <button onclick="editarPedido(${idx})">Editar</button>
                   <button onclick="quitarPedido(${idx})">Quitar</button>
               </td>
            `;
            tbody.appendChild(tr);
        });
        let totalCantidad = 0, totalVolumen = 0, totalPeso = 0, totalValor = 0;
        pedidosEnCurso.forEach(p => {
            totalCantidad += p.cantidad;
            totalVolumen += p.volumen;
            totalPeso += p.peso;
            totalValor += p.valor;
        });
        document.getElementById('totalesPedido').innerText = 
          `Total cantidad: ${totalCantidad} | Total volumen: ${totalVolumen.toFixed(3)} m³ | Total peso: ${totalPeso.toFixed(3)} kg | Total valor: $${totalValor.toFixed(2)}`;
         verificarCapacidad(totalVolumen, totalPeso);
    }
    function resetPedidoInputs() {
        document.getElementById('pedidoCodigoLlanta').value = '';
        document.getElementById('pedidoDescripcionLlanta').innerText = '';
        document.getElementById('pedidoCantidadLlanta').value = 1;
        document.getElementById('pedidoPesoLlanta').innerText = '0';
        document.getElementById('pedidoVolumenLlanta').innerText = '0';
        document.getElementById('pedidoValorUnitarioLlanta').innerText = '0';
    }

    // ----- Gráficas -----
    const ctxVolumen = document.getElementById('graphVolumen').getContext('2d');
    const ctxCarga = document.getElementById('graphCarga').getContext('2d');
    let chartVolumen = new Chart(ctxVolumen, {
        type: 'doughnut',
        data: { labels: ['Usado', 'Disponible'],
            datasets: [{ data: [0, 100], backgroundColor: ['#75c286', '#f3f3f3'], borderWidth: 1 }]
        },
        options: { plugins: {legend: {display: true}}, cutout: '70%' }
    });
    let chartCarga = new Chart(ctxCarga, {
        type: 'doughnut',
        data: { labels: ['Usado', 'Disponible'],
            datasets: [{ data: [0, 100], backgroundColor: ['#7ad4a2', '#f3f3f3'], borderWidth: 1 }]
        },
        options: { plugins: {legend: {display: true}}, cutout: '70%' }
    });   
  
    function actualizarGraficas() {
        if (!pedidoCamion) {
            chartVolumen.data.datasets[0].data = [0, 100];
            chartCarga.data.datasets[0].data = [0, 100];
        } else {
             let totalVolumen = pedidosEnCurso.reduce((acc, cur) => acc + cur.volumen, 0); // CORREGIDO
             let totalPeso = pedidosEnCurso.reduce((acc, cur) => acc + cur.peso, 0);
             let volTotal = +pedidoCamion["volumen"];
             let pesoTotal = +pedidoCamion["capacidad de carga (kg)"];
             chartVolumen.data.datasets[0].data = [Math.min(totalVolumen, volTotal), Math.max(0, volTotal - totalVolumen)];
             chartCarga.data.datasets[0].data = [Math.min(totalPeso, pesoTotal), Math.max(0, pesoTotal - totalPeso)];
        }
        chartVolumen.update(); chartCarga.update();
    }
function verificarCapacidad(volumen, peso) {
    if (!pedidoCamion) return;
    const capVol = +pedidoCamion.volumen;
    const capPes = +pedidoCamion["capacidad de carga (kg)"];
    const volumenPercent = (volumen / capVol) * 100,
        pesoPercent = (peso / capPes) * 100;

    // ALERTA si pasa el 85%
    if (volumenPercent > 85) {
        alert('¡Advertencia! Solo queda el 15% de espacio de volumen disponible en el camión.');
    }
    if (pesoPercent > 85) {
        alert('¡Advertencia! Solo queda el 15% de capacidad de carga disponible en el camión.');
    }

    if (volumenPercent > 80 || pesoPercent > 80) {
        if (confirm('El camión se está llenando (>85%), ¿desea completar con otro camión?')) {
            alert('Aquí puedes permitir solicitar otro camión para continuar cargando los pedidos.');
        }
    }
}

    // Modificada función aceptarPedido para guardar en SheetDB confirmados
    async function aceptarPedido() {
        if (!pedidoCamion) {
            alert('Debe seleccionar un camión válido para aceptar el pedido.');
            return;
        }
        if (pedidosEnCurso.length === 0) {
            alert('El pedido está vacío.');
            return;
        }

        let totalVolumen = pedidosEnCurso.reduce((acc, cur) => acc + cur.volumen, 0);
        let totalPeso = pedidosEnCurso.reduce((acc, cur) => acc + cur.peso, 0);
        let totalValor = pedidosEnCurso.reduce((acc, cur) => acc + cur.valor, 0);
        let totalCantidad = pedidosEnCurso.reduce((acc, cur) => acc + cur.cantidad, 0);

        const nuevoPedido = {
            camion: pedidoCamion.economico,
            llantas: pedidosEnCurso.map(p => p.clave).join(', '),
            descripcion: pedidosEnCurso.map(p => p.descripcion).join(', '),
            cantidad: pedidosEnCurso.map(p => p.cantidad).join(', '),
            linea: pedidosEnCurso.map(p => p.linea).join(', '),
            volumen: totalVolumen,
            peso: totalPeso,
            valor: totalValor,
            fecha: new Date().toLocaleDateString('es-MX'),
            "total,cantidad": totalCantidad
        };

        try {
            const res = await fetch('https://sheetdb.io/api/v1/lttpt3mvohen7?sheet=confirmados', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ data: nuevoPedido })
            });
            if (!res.ok) throw new Error('Error al guardar el pedido confirmado en la hoja de cálculo');

            pedidosConfirmados.push(nuevoPedido);
            pedidosEnCurso = [];
            pedidoCamion = null;
            document.getElementById('datosCamionPedido').innerText = '';
            document.getElementById('inputPedidoNumEconomico').value = '';
            renderPedidosActuales();
            actualizarGraficas();
            alert('Pedido aceptado y guardado en pedidos confirmados.');   c
            renderPedidosConfirmados();
        } catch (error) {
            alert('Error al guardar el pedido confirmado: ' + error.message);
        }
    }

    // -- Renderizar pedidos confirmados --
    function renderPedidosConfirmados() {
        const tbody = document.querySelector('#tabla tbody');
        tbody.innerHTML = '';
        pedidosConfirmados.forEach((pedido, idx) => {
            const tr = document.createElement('tr');
            tr.innerHTML = `
                <td>${pedido.camion}</td>
                <td>${pedido.llantas}</td>
                <td>${pedido.descripcion || ''}</td>
                <td>
                  <ul style="padding-left:18px;margin:0;">
                    ${pedido.cantidad
                      ? pedido.cantidad.split(',').map(q => `<li style="text-align:left;">${q.trim()}</li>`).join('')
                      : ''}
                 </ul>
                </td>
                <td>${pedido["total,cantidad"] || ''}</td>
                <td>${pedido.linea || ''}</td>
                <td>${Number(pedido.volumen).toLocaleString('es-MX', { minimumFractionDigits: 4, maximumFractionDigits: 4 })}</td>
                <td>${Number(pedido.peso).toLocaleString('es-MX', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}</td>
                <td>$${Number(pedido.valor).toLocaleString('es-MX', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}</td>
                <td>${pedido.fecha || ''}</td>
                <td><button onclick="cancelarPedido(${idx})">Cancelar</button></td>`;
            tbody.appendChild(tr);
        }); 
    }
    function cancelarPedido(idx) {
        if (confirm('¿Seguro que desea cancelar este pedido?')) {
            const pedidoACancelar = pedidosConfirmados[idx];
            // Opcional: Podrías agregar lógica para eliminar en SheetDB también
            pedidosConfirmados.splice(idx, 1);
            renderPedidosConfirmados();
        }
    }
</script>
         
<!-- Modal instrucciones -->
<div id="modalInstrucciones" class="modal">
  <div class="modal-content" style="max-width: 500px; padding: 20px;">
    <span class="close" onclick="cerrarInstrucciones()">&times;</span>
    <h2>Bienvenido al Sistema de Cubicaje Tres Siglos</h2>
    <p>Para empezar:</p>
    <ul>
      <li>En <b>Inventario</b>, consulta y agrega llantas.</li>
      <li>En <b>Flota</b>, administra camiones y capacidades.</li>
      <li>En <b>Pedidos</b>, gestiona la asignación de pedidos a las diferentes unidades controlando su volumen y capacidad de carga.</li>
      <li>En <b>Pedidos Confirmados</b>, revisa y gestiona los pedidos aceptados.</li>
    </ul>
    <p>Usa la barra de búsqueda para filtrar y los botones para agregar o actualizar datos.</p>
    <button onclick="cerrarInstrucciones()" style="background:#489051;color:white;padding:10px 15px;border:none;border-radius:5px;cursor:pointer;">Cerrar</button>
  </div>
</div>

<script>
    // Mostrar el modal con las instrucciones cada vez que se carga la página
    window.onload = function() {
      document.getElementById('modalInstrucciones').style.display = 'block';
    };

    // Función para cerrar el modal de instrucciones
    function cerrarInstrucciones() {
      document.getElementById('modalInstrucciones').style.display = 'none';
    }
// ...otras funciones...
// --- Procesar PDFs y extraer datos mejorados ---
let facturasExtraidas = [];

async function procesarFacturasPDF() {
    const input = document.getElementById('inputFacturasPDF');
    const files = input.files;
    if (!files.length) {
        alert('Selecciona uno o más archivos PDF.');
        return;
    }
    facturasExtraidas = [];
    for (let file of files) {
        try {
            const arrayBuffer = await file.arrayBuffer();
            const pdf = await pdfjsLib.getDocument({ data: arrayBuffer }).promise;
            let textoCompleto = '';
            let textoPorPagina = [];
            for (let i = 1; i <= pdf.numPages; i++) {
                const page = await pdf.getPage(i);
                const content = await page.getTextContent();
                const textoPagina = content.items.map(item => item.str).join('\n');
                textoCompleto += textoPagina + '\n';
                textoPorPagina.push({ page, textoPagina });
            }
            // Si el texto extraído es muy corto, intenta OCR
            if (textoCompleto.replace(/\s/g, '').length < 20) {
                textoCompleto = '';
                for (let i = 0; i < textoPorPagina.length; i++) {
                    const page = textoPorPagina[i].page;
                    const viewport = page.getViewport({ scale: 2 });
                    const canvas = document.createElement('canvas');
                    canvas.width = viewport.width;
                    canvas.height = viewport.height;
                    await page.render({ canvasContext: canvas.getContext('2d'), viewport }).promise;
                    // Usa Tesseract.js para OCR
                    const { data: { text } } = await Tesseract.recognize(canvas, 'spa');
                    textoCompleto += text + '\n';
                }
            }
            console.log('Texto extraído del PDF:', textoCompleto);

            // Extracción flexible con regex (ajusta según tu formato)
            const folioMatch = textoCompleto.match(/FOLIO\s*[:\-]?\s*([A-Z0-9\-]+)/i);
            const folio = folioMatch ? folioMatch[1].trim() : '';

            const fechaMatch = textoCompleto.match(/FECHA DE EMISI[ÓO]N?\s*[:\-]?\s*([\d\/\-\.\s:apm]+)/i);
            const fecha = fechaMatch ? fechaMatch[1].trim() : '';

            const usuarioMatch = textoCompleto.match(/USUARIO\s*[:\-]?\s*([A-ZÁÉÍÓÚÑ ]+)/i);
            const usuario = usuarioMatch ? usuarioMatch[1].trim() : '';

            const lineas = textoCompleto.split('\n');
            let productos = [];
            let productosEmpezaron = false;

            for (let i = 0; i < lineas.length; i++) {
                if (/CANTIDAD\s+C[ÓO]DIGO\s+DESCRIPCI[ÓO]N/i.test(lineas[i])) {
                    productosEmpezaron = true;
                    i++;
                    continue;
                }
                if (productosEmpezaron) {
                    let linea = lineas[i].trim();
                    if (!linea) break;
                    if (/TOTAL/i.test(linea)) break;

                    const partes = linea.split(/\s+/);
                    if (partes.length >= 3) {
                        const cantidad = partes[0];
                        const codigo = partes[1];
                        const descripcion = partes.slice(2).join(' ');

                        if (/^\d+$/.test(cantidad)) {
                            productos.push({ cantidad, codigo, descripcion });
                            continue;
                        }
                    }
                }
            }
            if (productos.length === 0) {
                productos.push({ cantidad: '', codigo: '', descripcion: '' });
            }
            productos.forEach(prod => {
                facturasExtraidas.push({
                    folio: folio || 'N/A',
                    fecha: fecha || 'N/A',
                    usuario: usuario || 'N/A',
                    cantidad: prod.cantidad,
                    codigo: prod.codigo,
                    descripcion: prod.descripcion,
                    fechaSubida: new Date().toLocaleDateString('es-MX')
                });
            });

        } catch (error) {
            alert('Error procesando el archivo ' + file.name + ': ' + error.message);
        }
    }
    renderTablaFacturas();
}
// ...resto de tus funciones...
function renderTablaFacturas() {
    const tbody = document.getElementById('tablaFacturas').querySelector('tbody');
    tbody.innerHTML = '';
    facturasExtraidas.forEach((f, idx) => {
        const tr = document.createElement('tr');
        tr.innerHTML = `
            <td><input value="${f.folio}" onchange="actualizarFacturaCampo(${idx},'folio',this.value)" /></td>
            <td><input value="${f.fecha}" onchange="actualizarFacturaCampo(${idx},'fecha',this.value)" /></td>
            <td><input value="${f.usuario}" onchange="actualizarFacturaCampo(${idx},'usuario',this.value)" /></td>
            <td><input type="number" value="${f.cantidad}" onchange="actualizarFacturaCampo(${idx},'cantidad',this.value)" /></td>
            <td><input value="${f.codigo}" onchange="actualizarFacturaCampo(${idx},'codigo',this.value)" /></td>
            <td><input value="${f.descripcion}" onchange="actualizarFacturaCampo(${idx},'descripcion',this.value)" /></td>
            <td>${f.fechaSubida}</td>
        `;
        tbody.appendChild(tr);
    });
}

function actualizarFacturaCampo(idx, campo, valor) {
    facturasExtraidas[idx][campo] = valor;
}

// --- Guardar facturas en SheetDB ---
async function guardarFacturas() {
    const lote = document.getElementById('nombreLoteFacturas').value.trim();
    if (!lote) {
        alert('Debes escribir un nombre/código para el lote.');
        return;
    }
    if (!facturasExtraidas.length) {
        alert('No hay facturas para guardar.');
        return;
    }
    try {
        for (let factura of facturasExtraidas) {
            factura.lote = lote; // agrega el nombre/código del lote
            await fetch('https://sheetdb.io/api/v1/lttpt3mvohen7?sheet=facturas', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ data: factura })
            });
        }
        alert('Facturas guardadas correctamente.');
        facturasExtraidas = [];
        renderTablaFacturas();
        document.getElementById('inputFacturasPDF').value = '';
        document.getElementById('nombreLoteFacturas').value = '';
    } catch (e) {
        alert('Error al guardar: ' + e.message);
    }
}
</script>
</body>
</html>
