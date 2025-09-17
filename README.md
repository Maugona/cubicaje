<!DOCTYPE html>
<html lang="es">
<head>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <meta charset="UTF-8" />
    <title>Sistema de cubicaje - Comercializadora de Llantas Tres Siglos</title>
    <link rel="icon" type="image/png" href="https://http2.mlstatic.com/storage/mshops-appearance-api/images/13/1184895213/logo-2022082314215812800.png">
    <style>
        /* --- Tus estilos existentes --- */
        body {
            font-family: Arial, sans-serif;
            margin: 0; padding: 0;
            background: url('https://llantas24.com/wp-content/uploads/2024/03/que-utilidad-tienen-las-llantas-de-un-carro.jpg') no-repeat center fixed;
            background-size: cover;
            /* Filtro para que no distraiga */
            filter: none;
        }
        section {
            background: rgba(255,255,255,0.55); /* Más transparente para que se vea la imagen */
            border-radius: 16px;
            margin: 32px auto 16px auto;
            max-width: 1200px;
            box-shadow: 0 8px 32px rgba(72,144,81,0.13);
            padding: 28px 22px;
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
            background: rgba(255,255,255,0.65); /* Menos opaco, se ve más la imagen */
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

        /* --- Estilos modernos para Facturas --- */
        .btn-gradient {
            background: linear-gradient(90deg, #2193b0 0%, #6dd5ed 100%);
            color: #fff;
            border: none;
            font-weight: bold;
            transition: background 0.3s;
        }
        .btn-gradient:hover {
            background: linear-gradient(90deg, #6dd5ed 0%, #2193b0 100%);
            color: #fff;
        }
        .card {
            border-radius: 1.5rem;
            box-shadow: 0 8px 32px rgba(33,147,176,0.15);
        }
        #facturaResult {
            animation: fadeIn 0.7s;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @import url('https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.5/font/bootstrap-icons.css');
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
    <button class="tablink" data-tab="pedidos">Pedidos</button>
    <button class="tablink" data-tab="pedidos-confirmados">Pedidos Confirmados</button>
    <button class="tablink" data-tab="facturas">Facturas</button> 
</nav>

<section>

    <!-- Inventario -->
    <div id="inventario" class="tabcontent active">
        <div class="search-and-button">
            <input type="text" id="searchInventario" class="search-bar" placeholder="Buscar por ID Llanta..." oninput="searchInventario()" />
            <button class="primary" onclick="openModal('modalInventario')">Agregar Llanta</button>
            <button class="primary" onclick="fetchInventario()">Actualizar inventario</button>
            <button class="primary" onclick="calcularVolumenInventario()">Calcular volumen de todas las llantas</button>
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

        <!-- Formulario para agregar llanta individual al pedido (necesario para las funciones JS) -->
        <div style="margin-bottom:12px; display:flex; gap:8px; align-items:end; flex-wrap:wrap;">
            <div style="display:flex;flex-direction:column;">
                <label for="pedidoCodigoLlanta">Código / Clave</label>
                <input type="text" id="pedidoCodigoLlanta" placeholder="Código o clave" oninput="autoCompletarLlantaPedidoPorCodigo()" />
            </div>
            <div style="display:flex;flex-direction:column;">
                <label for="pedidoDescripcionLlantaInput">Descripción</label>
                <input type="text" id="pedidoDescripcionLlantaInput" placeholder="Descripción" oninput="autoCompletarLlantaPedidoPorDescripcion()" />
            </div>
            <div style="display:flex;flex-direction:column; width:90px;">
                <label for="pedidoCantidadLlanta">Cantidad</label>
                <input type="number" id="pedidoCantidadLlanta" value="1" min="1" onchange="calcularTotalesPedido()" />
            </div>
            <div style="display:flex;flex-direction:column;">
                <label>Peso total</label>
                <div id="pedidoPesoLlanta">0</div>
            </div>
            <div style="display:flex;flex-direction:column;">
                <label>Volumen total</label>
                <div id="pedidoVolumenLlanta">0</div>
            </div>
            <div style="display:flex;flex-direction:column;">
                <label>Valor unitario</label>
                <div id="pedidoValorUnitarioLlanta">0</div>
            </div>
            <div>
                <button class="primary" onclick="agregarPedido()">Agregar al pedido</button>
            </div>
        </div>

        <!-- Campo para agregar bloque por folio -->
        <div style="margin-bottom: 10px;">
             <label for="inputFolioFacturaPedido"><b>Folio de Factura (autoagregar bloque):</b></label>
             <input type="text" id="inputFolioFacturaPedido" placeholder="Escribe el folio y presiona Enter" onkeydown="if(event.key==='Enter'){agregarBloquePorFolioPedido();return false;}" style="margin-left:8px;"/>
             <button class="primary" onclick="buscarBloquePorFolio()">Buscar bloque</button>
             <button class="primary" onclick="agregarBloquePorFolioPedido()">Agregar bloque por folio</button>
             <button class="primary" onclick="limpiarPedidosActuales()" style="background:#d9534f;">Limpiar</button>
             <div id="bloqueBuscadoPedido"></div>
        </div>

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
  <!-- OCR PDF para Facturas -->
<!-- Modernizado: OCR PDF para Facturas -->
<div class="tabcontent" id="facturas">
  <div class="container py-5">
    <div class="row justify-content-center">
      <div class="col-lg-12">
        <div class="card shadow-lg border-0 rounded-4">
          <div class="card-body p-4">
            <div class="d-flex align-items-center mb-3">
              <span class="me-2" style="font-size:2rem;color:#2193b0;">
                <i class="bi bi-file-earmark-pdf"></i>
              </span>
           <h2 class="mb-0 text-center flex-grow-1" style="color:#2193b0;">Escanea tus traspasos para ser más ágil el proceso de acomodo</h2>
           </div>
           <div class="mb-3">
               <label for="facturaPdfInput" class="form-label">Selecciona tu archivo PDF de factura</label>
               <input type="file" id="facturaPdfInput" accept="application/pdf" class="form-control" multiple>
           </div>
           <button id="facturaScanBtn" class="btn btn-gradient w-100 mb-3">
             <i class="bi bi-search"></i> Escanear y extraer texto
           </button>
           <!-- ...existing code... -->
           <button id="facturaClearBtn" class="btn btn-outline-danger w-100 mb-3">
             <i class="bi bi-x-circle"></i> Limpiar
           </button>
           <div class="mb-3 d-flex gap-2 align-items-center">
             <input type="text" id="facturaSearchFolio" class="form-control" placeholder="Buscar por número de folio..." />
             <input type="text" id="nombreBloqueFactura" class="form-control" placeholder="Nombre del bloque (ej: Facturas Julio 2025)">
             <button id="btnTerminarBloqueFactura" class="btn btn-success">Terminar y guardar bloque</button>
           </div>
           <!-- ...existing code... -->
           <div id="facturaLoading" class="text-center" style="display:none;">
             <div class="spinner-border text-info"></div>
             <p>Procesando...</p>
           </div>
           <progress id="facturaProgressBar" value="0" max="100" style="width:100%;height:22px;display:none;"></progress>
           <div id="facturaResult" class="mt-3" style="white-space:pre-wrap; background:#f7f7f7; border-radius:8px; padding:16px; min-height:80px;"></div>
           <div id="facturaGroupsContainer"></div>  
            <!-- Barra de avance para OCR Facturas -->
            <progress id="facturaProgressBar" value="0" max="100" style="width:100%;height:22px;display:none;"></progress>
            <div id="facturaResult" class="mt-3" style="white-space:pre-wrap; background:#f7f7f7; border-radius:8px; padding:16px; min-height:80px;"></div>
            <!-- Aquí va el contenedor de grupos -->
             <!-- Justo antes de <div id="facturaGroupsContainer"></div> -->
            <div id="facturaGroupsContainer"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
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
    // Helper: parsea valores que vienen de la hoja y devuelve número seguro (0 si no es numérico)
    function safeNum(v) {
        if (v === null || v === undefined) return 0;
        let s = String(v).trim();
        if (s === '') return 0;
        // Quita símbolo de moneda y espacios
        s = s.replace(/\$/g, '').replace(/\s+/g, '');
        // Si contiene ambos separadores, asumimos que las comas son separador de miles
        if (s.includes(',') && s.includes('.')) {
            s = s.replace(/,/g, '');
        } else if (s.includes(',') && !s.includes('.')) {
            // Probablemente usan coma como decimal
            s = s.replace(/,/g, '.');
        }
        // Elimina cualquier resto de comas
        s = s.replace(/,/g, '');
        const n = Number(s);
        return isNaN(n) ? 0 : n;
    }
    // Busca una propiedad entre varias alternativas comunes (tolerancia a nombres de columnas)
    function getField(obj, name) {
        if (!obj) return undefined;
        const keys = [name, name.toLowerCase(), name.toUpperCase(), name.charAt(0).toLowerCase() + name.slice(1)];
        // variantes comunes
        const variants = {
            volumen: ['volumen', 'Volumen', 'volumen (m3)', 'Volumen (m3)', 'volume'],
            peso: ['peso', 'Peso', 'weight', 'Weight'],
            valor: ['valor', 'Valor', 'precio', 'Precio', 'value']
        };
        const list = variants[name] || keys;
        for (const k of list) {
            if (k in obj) return obj[k];
        }
        // intenta buscar cualquier key que contenga el nombre
        for (const k of Object.keys(obj)) {
            if (k.toLowerCase().includes(name.toLowerCase())) return obj[k];
        }
        return undefined;
    }

// Pega aquí:
async function agregarBloquePorFolioPedido() {
    const folio = document.getElementById('inputFolioFacturaPedido').value.trim();
    if (!folio) {
        alert('Escribe un folio válido.');
        return;
    }
    // Busca el bloque en bloquesFacturas (ya cargados en la pestaña facturas)
    const bloque = bloquesFacturas.find(b => b.nombre === folio || (b.datos[0]?.Folio === folio));
    if (!bloque) {
        alert('No se encontró un bloque con ese folio.');
        return;
    }
    let agregadas = 0;
    bloque.datos.forEach(prod => {
        // Busca la llanta en inventario por clave/código
        const llanta = inventario.find(item => item.clave?.toString() === prod.Código?.toString());
        if (llanta) {
            // Verifica si ya está en pedidosEnCurso
            let pedidoExistente = pedidosEnCurso.find(p => p.clave === llanta.clave);
            const cantidad = Number(prod.Cantidad) || 1;
            if (pedidoExistente) {
                pedidoExistente.cantidad += cantidad;
                pedidoExistente.peso += safeNum(getField(llanta,'peso')) * cantidad;
                pedidoExistente.volumen += safeNum(getField(llanta,'volumen')) * cantidad;
                pedidoExistente.valor += safeNum(getField(llanta,'valor')) * cantidad;
            } else {
                pedidosEnCurso.push({
                    clave: llanta.clave,
                    descripcion: llanta.descripcion,
                    linea: llanta.linea || '',
                    cantidad: cantidad,
                    peso: safeNum(getField(llanta,'peso')) * cantidad,
                    volumen: safeNum(getField(llanta,'volumen')) * cantidad,
                    valor: safeNum(getField(llanta,'valor')) * cantidad
                });
            }
            agregadas++;
        }
    });
    if (agregadas > 0) {
        renderPedidosActuales();
        actualizarGraficas();
        alert(`Se agregaron ${agregadas} llantas del bloque "${folio}" al pedido.`);
    } else {
        alert('No se encontró ninguna llanta del bloque en el inventario.');
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
            const res = await fetch('https://sheetdb.io/api/v1/tblylxi4mrvid');
            if (!res.ok) throw new Error('Error al cargar inventario');
            inventario = await res.json();
            renderInventario();
        } catch (e) {
            alert('No se pudo cargar el inventario: ' + e.message);
        }
    }
    async function fetchFlota() {
        try {
            const res = await fetch('https://sheetdb.io/api/v1/tblylxi4mrvid?sheet=flota');
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
            const res = await fetch('https://sheetdb.io/api/v1/tblylxi4mrvid?sheet=confirmados');
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
    // (Se eliminó la definición duplicada de agregarBloquePorFolioPedido)
// ...existing code...
function renderInventario() {
    const tbody = document.querySelector('#tablaInventario tbody');
    tbody.innerHTML = '';
    inventario.forEach(llanta => {
        const tr = document.createElement('tr');
        // Si volumenGrande está marcado o volumen > 2, fondo azul claro
        if (llanta.volumenGrande || (safeNum(llanta.volumen) > 2)) {
            tr.style.background = '#cce6ff';
        }
        const pesoMostrar = (() => {
            const v = getField(llanta, 'peso');
            const n = safeNum(v);
            return (v === undefined || v === null || String(v).trim() === '') ? '-' : n.toFixed(3);
        })();
        const volumenMostrar = (() => {
            const v = getField(llanta, 'volumen');
            const n = safeNum(v);
            return (v === undefined || v === null || String(v).trim() === '') ? '-' : n.toFixed(3);
        })();
        const valorMostrar = (() => {
            const v = getField(llanta, 'valor');
            const n = safeNum(v);
            return (v === undefined || v === null || String(v).trim() === '') ? '-' : '$' + n.toFixed(2);
        })();

        tr.innerHTML = `
            <td>${llanta.clave}</td>
            <td>${llanta.descripcion}</td>
            <td>${llanta.linea || ''}</td>
            <td>${pesoMostrar}</td>
            <td>${volumenMostrar}</td>
            <td>${valorMostrar}</td>
            <td>
                <button onclick="editarLlanta('${llanta.clave}')">Editar</button>
                <button onclick="eliminarLlanta('${llanta.clave}')">Eliminar</button>
            </td>
        `;
        tbody.appendChild(tr);
    });
    highlightSearch('inventario', document.getElementById('searchInventario').value);
}
// ...existing code...

   async function eliminarLlanta(clave) {
     if (!confirm('¿Seguro que deseas eliminar esta llanta?')) return;
     try {
       const res = await fetch(`https://sheetdb.io/api/v1/tblylxi4mrvid/clave/${clave}`, {
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
// --- PEGA AQUÍ ---
// ...existing code...
async function calcularVolumenInventario() {
    inventario.sort((a, b) => Number(a.clave) - Number(b.clave));
    let noCalculadas = [];
    const updatedRows = []; // {clave, volumen}
    const failedRows = []; // {clave, descripcion, error}
    const margenLogistico = 1.40; // 40% extra por logística
    for (const llanta of inventario) {
        if (!llanta.volumen || Number(llanta.volumen) === 0) {
            let ancho, perfil, rin;
            let desc = (llanta.descripcion || '').replace(/[()]/g, '').toUpperCase();

            // 1. 185 60 R14 o 185/60 R14
            let m = desc.match(/(\d{3})[\/\s\-](\d{2})[\/\s\-]?R?(\d{2,2}\.?\d*)/);
            if (m) {
                ancho = Number(m[1]) / 1000; // a metros
                perfil = Number(m[2]) / 100;
                rin = Number(m[3]) * 0.0254; // a metros
            }
            // 2. 11R22.5, 12R24.5, 295 75 R22.5
            else if ((m = desc.match(/(\d{2,3})R(\d{2,2}\.?\d*)/))) {
                ancho = Number(m[1]) * 25.4 / 1000; // pulgadas a metros
                perfil = 0.80; // asume 80%
                rin = Number(m[2]) * 0.0254;
            }
            // 3. 31X10.50 R15, 33X12.50 R15
            else if ((m = desc.match(/(\d{2,3})[Xx](\d{2,3}\.?\d*)\s*R?(\d{2,2})/))) {
                rin = Number(m[1]) * 0.0254;
                ancho = Number(m[2]) * 25.4 / 1000;
                perfil = 0.80;
            }
            // 4. 7.50-16, 12.5/80-18, 14.9-24, 12-16.5
            else if ((m = desc.match(/(\d{1,2}\.?\d*)[\/\-](\d{2,3})[\- ](\d{2,2}\.?\d*)/))) {
                ancho = Number(m[1]) * 25.4 / 1000;
                perfil = 0.80;
                rin = Number(m[3]) * 0.0254;
            }
            // 5. 285/75 R24.5, 295/80 R22.5
            else if ((m = desc.match(/(\d{3})\/(\d{2})\s*R?(\d{2,2}\.?\d*)/))) {
                ancho = Number(m[1]) / 1000;
                perfil = Number(m[2]) / 100;
                rin = Number(m[3]) * 0.0254;
            }
            // 6. 14.9-24, 12-16.5 (sin perfil)
            else if ((m = desc.match(/(\d{1,2}\.?\d*)[\- ](\d{2,2}\.?\d*)/))) {
                ancho = Number(m[1]) * 25.4 / 1000;
                perfil = 0.80;
                rin = Number(m[2]) * 0.0254;
            }
            else {
                noCalculadas.push(llanta.descripcion || '(sin descripción)');
                continue;
            }

            // Altura flanco
            let alturaFlanco = perfil * ancho;
            // Diámetro externo
            let diametroExterno = rin + 2 * alturaFlanco;

            // Volumen tipo cubicaje (como en la imagen), con margen logístico
            let volumen_m3 = diametroExterno * diametroExterno * ancho * margenLogistico;

            // Actualiza en SheetDB (usa row_id cuando esté disponible). Si falla, intenta obtener row_id y reintentar.
            const newVol = volumen_m3.toFixed(4);
            try {
                if (llanta.row_id) {
                    console.log('Patch por row_id', llanta.row_id, 'clave', llanta.clave, '->', newVol);
                    const res = await fetch(`https://sheetdb.io/api/v1/tblylxi4mrvid/row_id/${encodeURIComponent(llanta.row_id)}`, {
                        method: 'PATCH',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify({ data: { volumen: newVol } })
                    });
                    if (!res.ok) throw new Error('PATCH falló con status ' + res.status);
                } else {
                    // Intenta obtener la fila para conocer su row_id
                    const key = encodeURIComponent(String(llanta.clave));
                    console.log('Buscando row para clave', llanta.clave);
                    const getRes = await fetch(`https://sheetdb.io/api/v1/tblylxi4mrvid/clave/${key}`);
                    if (!getRes.ok) throw new Error('GET row por clave falló con status ' + getRes.status);
                    const rows = await getRes.json();
                    if (Array.isArray(rows) && rows.length > 0 && rows[0].row_id) {
                        const rid = rows[0].row_id;
                        console.log('Obtuvo row_id', rid, 'para clave', llanta.clave, '- realizando PATCH');
                        const res2 = await fetch(`https://sheetdb.io/api/v1/tblylxi4mrvid/row_id/${encodeURIComponent(rid)}`, {
                            method: 'PATCH',
                            headers: { 'Content-Type': 'application/json' },
                            body: JSON.stringify({ data: { volumen: newVol } })
                        });
                        if (!res2.ok) throw new Error('PATCH (por row_id) falló con status ' + res2.status);
                    } else {
                        throw new Error('No se encontró row_id para clave ' + llanta.clave);
                    }
                }
                // Guarda en memoria
                llanta.volumen = newVol;
                updatedRows.push({ clave: llanta.clave, volumen: newVol });
                // Pequeña espera para evitar rate limits
                await new Promise(r => setTimeout(r, 120));
            } catch (err) {
                console.error('No se pudo actualizar volumen para clave', llanta.clave, err);
                const msg = `${llanta.clave} (${llanta.descripcion || 'sin descripción'}) - ${err.message}`;
                noCalculadas.push(msg);
                failedRows.push({ clave: llanta.clave, descripcion: llanta.descripcion || '', error: err.message });
            }
        }
    }
    renderInventario();

    // Genera CSV descargable con las filas actualizadas para import manual si las PATCH fallaron
    if (updatedRows.length > 0) {
        const csvLines = ['clave,volumen'];
        updatedRows.forEach(r => csvLines.push(`${JSON.stringify(r.clave)},${r.volumen}`));
        const csv = csvLines.join('\n');
        try {
            const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'volumen_updates.csv';
            document.body.appendChild(a);
            a.click();
            a.remove();
            URL.revokeObjectURL(url);
            console.log('CSV con actualizaciones descargado: volumen_updates.csv (contiene', updatedRows.length, 'filas)');
        } catch (e) {
            console.warn('No se pudo generar el CSV descargable:', e);
        }
    }
    if (noCalculadas.length > 0) {
        alert('No se pudo calcular el volumen de las siguientes llantas:\n' + noCalculadas.slice(0, 10).join('\n') + (noCalculadas.length > 10 ? '\n...y más' : ''));
    } else {
        alert('Volumen calculado y actualizado para todas las llantas que tenían volumen vacío (con margen de seguridad).');
    }
}
// ...existing code...
async function guardarEdicionLlanta(clave) {
  const nuevosDatos = {
    descripcion: document.getElementById('editDescripcion').value,
    linea: document.getElementById('editLinea').value,
    peso: document.getElementById('editPeso').value,
    volumen: document.getElementById('editVolumen').value,
    valor: document.getElementById('editValor').value
  };
  try {
    const res = await fetch(`https://sheetdb.io/api/v1/tblylxi4mrvid/clave/${clave}`, {
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

    const nuevoDato = { id, clave: id, descripcion, peso, volumen, valor, "Línea": Línea };

        try {
            const res = await fetch('https://sheetdb.io/api/v1/tblylxi4mrvid', {
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
        const cargaNum = safeNum(camion["capacidad de carga (kg)"] || camion.carga);
        const volumenNum = safeNum(camion["volumen"] || camion.volumen);
        const cargaMostrar = cargaNum === 0 ? '-' : cargaNum.toFixed(3);
        const volumenMostrar = volumenNum === 0 ? '-' : volumenNum.toFixed(3);
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
         const res = await fetch(`https://sheetdb.io/api/v1/tblylxi4mrvid/economico/${economico}?sheet=flota`, {
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
        const res = await fetch(`https://sheetdb.io/api/v1/tblylxi4mrvid/economico/${economico}?sheet=flota`, {
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
            const res = await fetch('https://sheetdb.io/api/v1/tblylxi4mrvid?sheet=flota', {
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
            document.getElementById('pedidoPesoLlanta').innerText = (safeNum(llanta.peso) * cantidad).toLocaleString('es-MX', {minimumFractionDigits: 2, maximumFractionDigits: 2});
            document.getElementById('pedidoVolumenLlanta').innerText = (safeNum(llanta.volumen) * cantidad).toLocaleString('es-MX', {minimumFractionDigits: 4, maximumFractionDigits: 4});
            document.getElementById('pedidoValorUnitarioLlanta').innerText = (safeNum(llanta.valor) * cantidad).toLocaleString('es-MX', {minimumFractionDigits: 2, maximumFractionDigits: 2});
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
    const pedidoExistente = pedidosEnCurso.find(p => p.id === llanta.clave || p.clave === llanta.clave);
        if (pedidoExistente) {
            pedidoExistente.cantidad += cantidad;
                pedidoExistente.peso += safeNum(getField(llanta,'peso')) * cantidad;
                pedidoExistente.volumen += safeNum(getField(llanta,'volumen')) * cantidad;
                pedidoExistente.valor += safeNum(getField(llanta,'valor')) * cantidad;
        } else {
            pedidosEnCurso.push({
                clave: llanta.clave,
                descripcion: llanta.descripcion,
                linea: llanta.linea || '',
                cantidad: cantidad,
                    peso: safeNum(getField(llanta,'peso')) * cantidad,
                    volumen: safeNum(getField(llanta,'volumen')) * cantidad,
                    valor: safeNum(getField(llanta,'valor')) * cantidad
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
        pedido.peso = safeNum(getField(llanta,'peso')) * nuevaCantidad;
    pedido.volumen = safeNum(getField(llanta,'volumen')) * nuevaCantidad;
    pedido.valor = safeNum(getField(llanta,'valor')) * nuevaCantidad;

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
                       <td>${(pedido.volumen || pedido.volumen===0) ? safeNum(pedido.volumen).toLocaleString('es-MX', { minimumFractionDigits: 3, maximumFractionDigits: 3 }) : '-'}</td>
                       <td>${(pedido.peso || pedido.peso===0) ? safeNum(pedido.peso).toLocaleString('es-MX', { minimumFractionDigits: 3, maximumFractionDigits: 3 }) : '-'}</td>
                   <td>${(pedido.valor || pedido.valor===0) ? ('$' + safeNum(pedido.valor).toLocaleString('es-MX', { minimumFractionDigits: 2, maximumFractionDigits: 2 })) : '-'}</td>
               <td>
                   <button onclick="editarPedido(${idx})">Editar</button>
                   <button onclick="quitarPedido(${idx})">Quitar</button>
               </td>
            `;
            tbody.appendChild(tr);
        });
        let totalCantidad = 0, totalVolumen = 0, totalPeso = 0, totalValor = 0;
        pedidosEnCurso.forEach(p => {
            totalCantidad += safeNum(p.cantidad);
            totalVolumen += safeNum(p.volumen);
            totalPeso += safeNum(p.peso);
            totalValor += safeNum(p.valor);
        });
      // ...dentro de function renderPedidosActuales()...
    document.getElementById('totalesPedido').innerText = 
      `Total cantidad: ${totalCantidad.toLocaleString('es-MX')} | Total volumen: ${totalVolumen.toLocaleString('es-MX', { minimumFractionDigits: 3, maximumFractionDigits: 3 })} m³ | Total peso: ${totalPeso.toLocaleString('es-MX', { minimumFractionDigits: 3, maximumFractionDigits: 3 })} kg | Total valor: $${totalValor.toLocaleString('es-MX', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}`;
         verificarCapacidad(totalVolumen, totalPeso);
    }
    function resetPedidoInputs() {
        document.getElementById('pedidoCodigoLlanta').value = '';
        document.getElementById('pedidoDescripcionLlantaInput').value = '';
        document.getElementById('pedidoCantidadLlanta').value = 1;
        document.getElementById('pedidoPesoLlanta').innerText = '0';
        document.getElementById('pedidoVolumenLlanta').innerText = '0';
        document.getElementById('pedidoValorUnitarioLlanta').innerText = '0';
    }
    // ...después de function renderPedidosActuales()...
    function limpiarPedidosActuales() {
    if (confirm('¿Seguro que deseas limpiar todos los pedidos actuales del camión?')) {
        pedidosEnCurso = [];
        renderPedidosActuales();
        actualizarGraficas();
    }
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
             let totalVolumen = pedidosEnCurso.reduce((acc, cur) => acc + safeNum(cur.volumen), 0);
             let totalPeso = pedidosEnCurso.reduce((acc, cur) => acc + safeNum(cur.peso), 0);
             let volTotal = safeNum(pedidoCamion["volumen"] || pedidoCamion.volumen);
             let pesoTotal = safeNum(pedidoCamion["capacidad de carga (kg)"] || pedidoCamion["carga"] || pedidoCamion.carga);
             chartVolumen.data.datasets[0].data = [Math.min(totalVolumen, volTotal), Math.max(0, volTotal - totalVolumen)];
             chartCarga.data.datasets[0].data = [Math.min(totalPeso, pesoTotal), Math.max(0, pesoTotal - totalPeso)];
        }
        chartVolumen.update(); chartCarga.update();
    }
function verificarCapacidad(volumen, peso) {
    if (!pedidoCamion) return;
    const capVol = safeNum(pedidoCamion.volumen || pedidoCamion["volumen"]);
    const capPes = safeNum(pedidoCamion["capacidad de carga (kg)"] || pedidoCamion.carga || pedidoCamion["carga"]);
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

             let totalVolumen = pedidosEnCurso.reduce((acc, cur) => acc + safeNum(cur.volumen), 0);
             let totalPeso = pedidosEnCurso.reduce((acc, cur) => acc + safeNum(cur.peso), 0);
             let totalValor = pedidosEnCurso.reduce((acc, cur) => acc + safeNum(cur.valor), 0);
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
            const res = await fetch('https://sheetdb.io/api/v1/tblylxi4mrvid?sheet=confirmados', {
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
            alert('Pedido aceptado y guardado en pedidos confirmados.');
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
            <td>${Number(pedido.volumen).toLocaleString('es-MX', { minimumFractionDigits: 3, maximumFractionDigits: 3 })}</td>
            <td>${Number(pedido.peso).toLocaleString('es-MX', { minimumFractionDigits: 3, maximumFractionDigits: 3 })}</td>
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
      <li>En <b>Facturas</b>, escanea tus traspasos para después generar  el cubicaje correspondiente.</li>
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
</script>
<script src="https://cdn.jsdelivr.net/npm/pdfjs-dist@3.11.174/build/pdf.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/tesseract.js@5.0.4/dist/tesseract.min.js"></script>
<script>
// ...existing code...

// Variables globales para Facturas OCR
const facturaPdfInput = document.getElementById('facturaPdfInput');
const facturaScanBtn = document.getElementById('facturaScanBtn');
const facturaResultDiv = document.getElementById('facturaResult');
const facturaLoadingDiv = document.getElementById('facturaLoading');
const facturaClearBtn = document.getElementById('facturaClearBtn');
const facturaProgressBar = document.getElementById('facturaProgressBar');
let bloquesFacturas = []; // [{nombre, datos: [facturas]}]
let archivosEscaneados = []; // [{nombreArchivo, productos: [...] }]
let facturasParaGuardar = [];

// Botón Limpiar
// ...existing code...
facturaClearBtn.onclick = () => {
    facturaPdfInput.value = '';
    facturaResultDiv.textContent = '';
    archivosEscaneados = [];
    facturasParaGuardar = [];
    mostrarArchivosEscaneados();
    facturaLoadingDiv.style.display = 'none'; // <-- agrega esto para ocultar el spinner
    facturaProgressBar.style.display = 'none';
    // NO borres bloquesFacturas aquí
};
// ...existing code...

// Función para agregar productos nuevos del escaneo al inventario
async function agregarNuevosProductosAlInventario(productos) {
    try {
        // 1. Obtener inventario actual
        const res = await fetch('https://sheetdb.io/api/v1/tblylxi4mrvid');
        if (!res.ok) throw new Error('No se pudo cargar inventario');
        const inventarioActual = await res.json();

        // 2. Filtrar productos que no estén en inventario (por Código)
        const codigosInventario = inventarioActual.map(item => item.clave?.trim());
        const nuevos = productos.filter(p => !codigosInventario.includes(p.Código?.trim()));

        // 3. Preparar datos para inventario
        const nuevosDatos = nuevos.map(p => ({
            clave: p.Código?.trim(),
            descripcion: p.Descripción?.trim(),
            linea: '', // Puedes intentar extraer la línea si tienes ese dato
            peso: '',  // Si tienes el peso en el escaneo, agrégalo aquí
            volumen: '', // Si tienes el volumen, agrégalo aquí
            valor: '' // Si tienes el valor, agrégalo aquí
        }));

        // 4. Enviar solo si hay nuevos
        if (nuevosDatos.length > 0) {
            await fetch('https://sheetdb.io/api/v1/tblylxi4mrvid', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ data: nuevosDatos })
            });
        }
    } catch (e) {
        console.error('Error al agregar nuevos productos al inventario:', e);
    }
}

// ...dentro de facturaScanBtn.onclick...
// Escanear y mostrar tabla + barra para nombre
// ...existing code...
facturaScanBtn.onclick = async () => {
    const files = Array.from(facturaPdfInput.files);
    if (files.length === 0) {
        alert('Por favor, selecciona al menos un archivo PDF.');
        return;
    }
    facturaLoadingDiv.style.display = 'block';
    facturaProgressBar.style.display = 'block';
    facturaProgressBar.value = 0;
    facturaProgressBar.max = 100;
    // NO borres archivosEscaneados aquí

    try {
        for (let i = 0; i < files.length; i++) {
            const file = files[i];
            const reader = new FileReader();
            await new Promise(resolve => {
                reader.onload = async function() {
                    const typedarray = new Uint8Array(this.result);
                    const pdf = await pdfjsLib.getDocument(typedarray).promise;
                    let extractedText = '';
                    for (let pageNum = 1; pageNum <= pdf.numPages; pageNum++) {
                        const page = await pdf.getPage(pageNum);
                        const viewport = page.getViewport({ scale: 2 });
                        const canvas = document.createElement('canvas');
                        const context = canvas.getContext('2d');
                        canvas.width = viewport.width;
                        canvas.height = viewport.height;
                        await page.render({ canvasContext: context, viewport: viewport }).promise;
                        const dataUrl = canvas.toDataURL();
                        const { data: { text } } = await Tesseract.recognize(dataUrl, 'spa', {
                            logger: m => {
                                facturaProgressBar.value = Math.round(m.progress * 100);
                                facturaLoadingDiv.innerHTML = `<div class="spinner-border text-info"></div><p>PDF ${i+1} - ${m.status}: ${Math.round(m.progress*100)}%</p>`;
                            }
                        });
                        extractedText += text + '\n';
                    }
                    const folio = (extractedText.match(/FOLIO\s*[:\-]?\s*([A-Za-z0-9\-]+)/i) || [])[1] || '';
                    const fecha = (extractedText.match(/FECHA DE EMISION\s*[:\-]?\s*([0-9\/\:\. ]+)/i) || [])[1] || '';
                    const usuario = (extractedText.match(/USUARIO\s*[:\-]?\s*([A-Za-z\s]+)/i) || [])[1] || '';

                    // Limpia el texto antes de aplicar el regex
                    let textoLimpio = extractedText
                       .replace(/\r/g, '')
                       .replace(/[ ]{2,}/g, ' ')
                       .replace(/^\s*$/gm, '');

                    // Regex mejorado para filas tipo tabla
                    const productoRegex = /^\s*(\d+)\s+([A-Za-z0-9\-]+)\s+(.+)$/gm;
                    let productos = [];
                    let match;
                    while ((match = productoRegex.exec(textoLimpio)) !== null) {
                        // Filtra encabezados y filas vacías
                        if (
                            match[2].toUpperCase() === 'CÓDIGO' ||
                            match[3].toUpperCase() === 'DESCRIPCIÓN' ||
                            !match[2] || !match[3]
                        ) continue;
                        productos.push({
                            Folio: folio,
                            "Fecha de Emisión": fecha,
                            Usuario: usuario,
                            Cantidad: match[1],
                            Código: match[2],
                            Descripción: match[3].trim()
                        });
                    } 
                    archivosEscaneados.push({ nombreArchivo: file.name, productos });
                    mostrarArchivosEscaneados();
                    resolve();
                };
                reader.readAsArrayBuffer(file);
            });
        }
        // Actualiza productos acumulados para guardar
        facturasParaGuardar = archivosEscaneados.flatMap(a => a.productos);
    } catch (e) {
        alert('Ocurrió un error durante el escaneo: ' + e.message);
    } finally {
        facturaLoadingDiv.style.display = 'none';
        facturaProgressBar.style.display = 'none';
    }
};
    
    mostrarArchivosEscaneados();

    // Muestra TODOS los productos acumulados
    let html = `<h5 class="mt-4 mb-2">Productos acumulados en el bloque:</h5>
        <table class="table table-bordered">
            <thead>
                <tr>
                    <th>Folio</th>
                    <th>Fecha de Emisión</th>
                    <th>Usuario</th>
                    <th>Cantidad</th>
                    <th>Código</th>
                    <th>Descripción</th>
                </tr>
            </thead>
            <tbody>`;
    facturasParaGuardar.forEach((p, idx) => {
        html += `<tr>
            <td>${p.Folio}</td>
            <td>${p["Fecha de Emisión"]}</td>
            <td>${p.Usuario}</td>
            <td>${p.Cantidad}</td>
            <td>${p.Código}</td>
            <td>${p.Descripción}</td>
        </tr>`;
    });
    html += '</tbody></table>';

// ...existing code...
document.getElementById('btnTerminarBloqueFactura').onclick = async () => {
    const nombreBloque = document.getElementById('nombreBloqueFactura').value.trim() || 'Sin nombre';
    facturasParaGuardar = archivosEscaneados.flatMap(a => a.productos);
    if (facturasParaGuardar.length === 0) {
        alert('No hay productos para guardar.');
        return;
    }
    // Agrega el nombre del bloque a cada producto
     facturasParaGuardar.forEach(p => p.Nombre = nombreBloque);

    bloquesFacturas.push({ nombre: nombreBloque, datos: facturasParaGuardar });
    await guardarFacturasEnSheetDB(facturasParaGuardar);
    await agregarNuevosProductosAlInventario(facturasParaGuardar);
    facturaResultDiv.textContent = '';
    archivosEscaneados = [];
    facturasParaGuardar = [];
    mostrarArchivosEscaneados();
    mostrarBloquesFacturas();
};
// ...existing code...
// filepath: c:\Users\mg296\OneDrive\Escritorio\cubicaja\Proyecto_de_residencia_profesional.html
// ...existing code...
// Guardar en SheetDB (más rápido: POST en lote)
async function guardarFacturasEnSheetDB(facturas) {
    try {
        await fetch('https://sheetdb.io/api/v1/tblylxi4mrvid?sheet=facturas', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ data: facturas }) // Enviar array
        });
    } catch (e) {
        console.error('Error al guardar facturas:', e);
    }
}
// ...existing code...
function mostrarArchivosEscaneados() {
    let html = `<h5 class="mt-4 mb-2">Archivos escaneados:</h5>`;
    archivosEscaneados.forEach((archivo, idx) => {
        html += `
            <div style="margin-bottom:8px;">
                <b>${archivo.nombreArchivo}</b>
                <button class="btn btn-danger btn-sm" onclick="eliminarArchivoEscaneado(${idx})">Eliminar</button>
                <table class="table table-bordered mt-2">
                    <thead>
                        <tr>
                            <th>Folio</th>
                            <th>Fecha de Emisión</th>
                            <th>Usuario</th>
                            <th>Cantidad</th>
                            <th>Código</th>
                            <th>Descripción</th>
                        </tr>
                    </thead>
                    <tbody>
                        ${archivo.productos.map(p => `
                            <tr>
                                <td>${p.Folio}</td>
                                <td>${p["Fecha de Emisión"]}</td>
                                <td>${p.Usuario}</td>
                                <td>${p.Cantidad}</td>
                                <td>${p.Código}</td>
                                <td>${p.Descripción}</td>
                            </tr>
                        `).join('')}
                    </tbody>
                </table>
            </div>
        `;
    });
    
    facturaResultDiv.innerHTML = html;


}

function eliminarArchivoEscaneado(idx) {
    archivosEscaneados.splice(idx, 1);
    facturaPdfInput.value = ''; // Limpia el input de archivos
    mostrarArchivosEscaneados();
}

// Mostrar todos los bloques en la página
function mostrarBloquesFacturas(filtro = '') {
    const container = document.getElementById('facturaGroupsContainer');
    container.innerHTML = '';
    bloquesFacturas
        .filter(b => b.nombre.toLowerCase().includes(filtro.toLowerCase()))
        .forEach((bloque, idx) => {
        let html = `
            <div class="card mb-2" id="bloqueFactura${idx}">
                <div class="card-header d-flex justify-content-between align-items-center" style="cursor:pointer;" onclick="toggleDetalleBloque(${idx})">
                    <strong>${bloque.nombre}</strong>
                    <span style="font-size:1.2em;">&#x25BC;</span>
                    <button class="btn btn-danger btn-sm" onclick="event.stopPropagation(); eliminarBloqueFactura(${idx})">Eliminar bloque</button>
                </div>
                <div class="card-body" id="detalleBloque${idx}" style="display:none;">
                    <table class="table table-bordered">
                        <thead>
                            <tr>
                                <th>Folio</th>
                                <th>Fecha de Emisión</th>
                                <th>Usuario</th>
                                <th>Cantidad</th>
                                <th>Código</th>
                                <th>Descripción</th>
                            </tr>
                        </thead>
                        <tbody>
                           ${bloque.datos.map((f, idx) => `
                               <tr>
                                   <td>${idx === 0 ? f.Folio : ''}</td>
                                   <td>${idx === 0 ? f["Fecha de Emisión"] : ''}</td>
                                   <td>${idx === 0 ? f.Usuario : ''}</td>
                                   <td>${f.Cantidad || ''}</td>
                                   <td>${f.Código || ''}</td>
                                   <td>${f.Descripción || ''}</td>
                               </tr>
                           `).join('')}
                       </tbody>
                   </table>
               </div>
            </div>
        `;
        container.innerHTML += html;
    });
}

// Agrega esta función para expandir/colapsar el detalle
function toggleDetalleBloque(idx) {
    const detalle = document.getElementById('detalleBloque' + idx);
    if (detalle.style.display === 'none') {
        detalle.style.display = 'block';
    } else {
        detalle.style.display = 'none';
    }
}
// Eliminar bloque de la página y de la hoja de cálculo
// filepath: c:\Users\mg296\OneDrive\Escritorio\cubicaja\Proyecto_de_residencia_profesional.html
// ...existing code...
async function eliminarBloqueFactura(idx) {
    if (!confirm('¿Seguro que deseas eliminar este bloque de facturas?')) return;
    const bloque = bloquesFacturas[idx];
    const nombreBloque = (bloque.nombre || '').trim().toLowerCase();

    // 1. Obtén todas las filas con ese nombre
    let errores = 0;
    try {
        const res = await fetch(`https://sheetdb.io/api/v1/tblylxi4mrvid/Nombre/${encodeURIComponent(nombreBloque)}?sheet=facturas`);
        const facturas = await res.json();
        // 2. Elimina cada una por su row_id
        for (const factura of facturas) {
            if (factura.row_id) {
                const delRes = await fetch(`https://sheetdb.io/api/v1/tblylxi4mrvid/row_id/${factura.row_id}?sheet=facturas`, {
                    method: 'DELETE'
                });
                if (!delRes.ok) errores++;
            }
        }
    } catch (e) {
        errores = bloque.datos.length;
    }
    bloquesFacturas.splice(idx, 1);
    mostrarBloquesFacturas();
    if (errores > 0) {
        alert(`El bloque se eliminó de la página, pero ${errores} factura(s) no se pudieron eliminar de la hoja de cálculo.`);
    } else {
        alert('Bloque eliminado correctamente de la página y la hoja de cálculo.');
    }
}
// ...existing code...
// Buscar bloques por nombre
document.getElementById('facturaSearchFolio').addEventListener('input', function() {
    mostrarBloquesFacturas(this.value);
});

// Al cargar la pestaña, carga los bloques desde SheetDB
document.querySelector('button[data-tab="facturas"]').addEventListener('click', async () => {
    try {
        const res = await fetch('https://sheetdb.io/api/v1/tblylxi4mrvid?sheet=facturas');
        if (!res.ok) throw new Error('No se pudo cargar facturas');
        const facturas = await res.json();
        bloquesFacturas = [];
        let grupos = {};
        facturas.forEach(f => {
            // Agrupa por 'Nombre' (mayúscula inicial)
            const grupo = f.Nombre || f.Folio || f["Fecha de Emisión"] || 'Sin nombre';
            if (!grupos[grupo]) grupos[grupo] = [];
            grupos[grupo].push(f);
        });
        for (const nombre in grupos) {
            bloquesFacturas.push({ nombre, datos: grupos[nombre] });
        }
        mostrarBloquesFacturas();
    } catch (e) {
        document.getElementById('facturaGroupsContainer').innerHTML = '<div class="alert alert-danger">No se pudo cargar facturas guardadas.</div>';
    }
});
// ...existing code...
</script>
</body>
</html>
