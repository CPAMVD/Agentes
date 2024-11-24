- 👋 Hi, I’m @CPAMVD
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
CPAMVD/CPAMVD is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<html><head><base href="."><meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sistema ERP Empresarial</title>
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdn.jsdelivr.net/npm/xlsx@0.18.5/dist/xlsx.full.min.js"></script>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
<link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.7.2/font/bootstrap-icons.css" rel="stylesheet">

<style>
:root {
    --primary-color: #2c3e50;
    --secondary-color: #34495e;
    --accent-color: #3498db;
    --success-color: #2ecc71;
    --warning-color: #f1c40f;
    --danger-color: #b9e90e;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f5f6fa;
}

.sidebar {
    background: var(--primary-color);
    min-height: 100vh;
    padding: 20px 0;
    transition: all 0.3s;
}

.sidebar .nav-link {
    color: #fff;
    padding: 10px 20px;
    transition: all 0.3s;
}

.sidebar .nav-link:hover {
    background: var(--secondary-color);
    padding-left: 25px;
}

.sidebar .nav-link i {
    margin-right: 10px;
}

.main-content {
    padding: 20px;
}

.module-card {
    background: #fff;
    border-radius: 10px;
    padding: 15px; /* Reduced from 20px */
    margin-bottom: 15px; /* Reduced from 20px */
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    transition: transform 0.3s;
}

.module-card:hover {
    transform: translateY(-5px);
}

.stats-card {
    background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
    color: white;
}

.notification-badge {
    position: absolute;
    top: -5px;
    right: -5px;
    background: var(--danger-color);
}

.user-profile {
    padding: 20px;
    text-align: center;
    color: white;
    border-bottom: 1px solid rgba(255,255,255,0.1);
}

.user-profile img {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    margin-bottom: 10px;
}

.dashboard-chart {
    height: 300px;
    margin-bottom: 20px;
}

.custom-table {
    background: white;
    border-radius: 10px;
    overflow: hidden;
}

.module-icon {
    font-size: 1.5em; /* Reduced from 2em */
    margin-bottom: 10px; /* Reduced from 15px */
    color: var(--accent-color);
}

.loading-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0,0,0,0.7);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
}

.spinner {
    width: 50px;
    height: 50px;
    border: 5px solid #f3f3f3;
    border-top: 5px solid var(--accent-color);
    border-radius: 50%;
    animation: spin 1s linear infinite;
}

@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

.cuenta-nivel-1 {
    font-weight: bold;
    background-color: #f8f9fa;
}

.cuenta-nivel-2 {
    padding-left: 20px;
    background-color: #ffffff;
}

.cuenta-nivel-3 {
    padding-left: 40px;
    background-color: #ffffff;
}

.cuenta-nivel-4 {
    padding-left: 60px;
    background-color: #ffffff;
}

.cuenta-nivel-5 {
    padding-left: 80px;
    background-color: #ffffff;
}

.tax-configuration {
    border: 1px solid #dee2e6;
    border-radius: 4px;
    padding: 15px;
    margin-top: 15px;
}

.tax-configuration h6 {
    margin-bottom: 15px;
    color: var(--primary-color);
}

.tax-configuration .form-control-sm {
    height: 25px;
    padding: 2px 5px;
}

.tax-configuration .table td {
    vertical-align: middle;
}

.tax-configuration .form-check-input {
    margin-top: 0;
}

@media print {
    body * {
        visibility: hidden;
    }
    #printInvoice, #printInvoice * {
        visibility: visible;
    }
    #printInvoice {
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
    }
    .no-print {
        display: none !important;
    }
}

.invoice-header {
    text-align: center;
    margin-bottom: 20px;
}

.invoice-logo {
    max-width: 200px;
    margin-bottom: 10px;
}

.invoice-company-info {
    margin-bottom: 20px;
}

.invoice-details {
    margin-bottom: 20px;
    padding: 10px;
    border: 1px solid #ddd;
}

.invoice-items-table {
    width: 100%;
    margin-bottom: 20px;
    border-collapse: collapse;
}

.invoice-items-table th,
.invoice-items-table td {
    border: 1px solid #ddd;
    padding: 8px;
}

.invoice-totals {
    float: right;
    width: 300px;
}

.invoice-footer {
    clear: both;
    margin-top: 40px;
    text-align: center;
    font-size: 12px;
}
</style>
</head>
<body>

<div class="container-fluid">
    <div class="row">
        <!-- Sidebar -->
        <div class="col-md-2 sidebar">
            <div class="user-profile">
                <img src="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' width='80' height='80'><rect width='80' height='80' fill='%234a69bd'/><text x='40' y='45' font-size='35' text-anchor='middle' fill='white'>JD</text></svg>" alt="User Profile">
                <h6>John Doe</h6>
                <small>Administrador</small>
            </div>
            
            <ul class="nav flex-column mt-4">
                <li class="nav-item">
                    <a class="nav-link active" href="#dashboard">
                        <i class="bi bi-house-door"></i> Dashboard
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#contabilidad">
                        <i class="bi bi-journal-text"></i> Contabilidad
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#clientes">
                        <i class="bi bi-people"></i> Clientes
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#proveedores">
                        <i class="bi bi-truck"></i> Proveedores
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#bancos">
                        <i class="bi bi-bank"></i> Bancos
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#nominas">
                        <i class="bi bi-person-badge"></i> Nóminas
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#activos">
                        <i class="bi bi-building"></i> Activos Fijos
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#inventarios">
                        <i class="bi bi-box-seam"></i> Inventarios
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#compras">
                        <i class="bi bi-cart"></i> Compras
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#ventas">
                        <i class="bi bi-graph-up"></i> Ventas
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#parametros">
                        <i class="bi bi-gear"></i> Parámetros
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#reportes">
                        <i class="bi bi-file-earmark-text"></i> Reportes
                    </a>
                </li>
            </ul>
        </div>

        <!-- Main Content -->
        <div class="col-md-10 main-content">
            <div class="row mb-4">
                <div class="col-md-12">
                    <h2>Dashboard</h2>
                    <hr>
                </div>
            </div>

            <!-- Stats Cards -->
            <div class="row mb-4">
                <div class="col-md-3">
                    <div class="module-card stats-card">
                        <h4>Ventas del Mes</h4>
                        <h2>$124,500</h2>
                        <p><i class="bi bi-arrow-up"></i> 12% vs mes anterior</p>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="module-card stats-card">
                        <h4>Clientes Activos</h4>
                        <h2>1,234</h2>
                        <p><i class="bi bi-people"></i> +15 nuevos este mes</p>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="module-card stats-card">
                        <h4>Órdenes Pendientes</h4>
                        <h2>45</h2>
                        <p><i class="bi bi-clock"></i> 12 urgentes</p>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="module-card stats-card">
                        <h4>Inventario</h4>
                        <h2>$345,600</h2>
                        <p><i class="bi bi-box"></i> 85% capacidad</p>
                    </div>
                </div>
            </div>

            <!-- Charts -->
            <div class="row mb-4">
                <div class="col-md-6">
                    <div class="module-card">
                        <h4>Ventas vs Tiempo</h4>
                        <canvas id="salesChart" class="dashboard-chart"></canvas>
                    </div>
                </div>
                <div class="col-md-6">
                    <div class="module-card">
                        <h4>Distribución de Ingresos</h4>
                        <canvas id="incomeChart" class="dashboard-chart"></canvas>
                    </div>
                </div>
            </div>

            <!-- Recent Activities Table -->
            <div class="row">
                <div class="col-md-12">
                    <div class="module-card">
                        <h4>Actividades Recientes</h4>
                        <div class="table-responsive">
                            <table class="table custom-table">
                                <thead>
                                    <tr>
                                        <th>ID</th>
                                        <th>Actividad</th>
                                        <th>Usuario</th>
                                        <th>Fecha</th>
                                        <th>Estado</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td>#1234</td>
                                        <td>Nueva venta registrada</td>
                                        <td>Juan Pérez</td>
                                        <td>2023-07-20 14:30</td>
                                        <td><span class="badge bg-success">Completado</span></td>
                                    </tr>
                                    <tr>
                                        <td>#1233</td>
                                        <td>Actualización de inventario</td>
                                        <td>María González</td>
                                        <td>2023-07-20 13:15</td>
                                        <td><span class="badge bg-warning">Pendiente</span></td>
                                    </tr>
                                    <tr>
                                        <td>#1232</td>
                                        <td>Pago a proveedor</td>
                                        <td>Carlos Ruiz</td>
                                        <td>2023-07-20 11:45</td>
                                        <td><span class="badge bg-success">Completado</span></td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Contabilidad Module -->
            <div id="contabilidad-module" class="module-content" style="display: none;">
                <div class="row mb-4">
                    <div class="col-md-12">
                        <h2>Contabilidad</h2>
                        <hr>
                    </div>
                </div>

                <!-- Horizontal Menu Cards -->
                <div class="row mb-4">
                    <div class="col-md-2">
                        <div class="module-card text-center">
                            <i class="bi bi-journal-text module-icon"></i>
                            <h5>Plan de Cuentas</h5>
                            <button class="btn btn-primary btn-sm mt-2" onclick="manageCostCenters()">
                                <i class="bi bi-gear"></i> Gestionar Centros de Costos
                            </button>
                            <button class="btn btn-primary btn-sm mt-2">Acceder</button>
                        </div>
                    </div>
                    <div class="col-md-2">
                        <div class="module-card text-center">
                            <i class="bi bi-journal module-icon"></i>
                            <h5>Diario</h5>
                            <button class="btn btn-primary btn-sm mt-2">Acceder</button>
                        </div>
                    </div>
                    <div class="col-md-2">
                        <div class="module-card text-center">
                            <i class="bi bi-book module-icon"></i>
                            <h5>Mayor General</h5>
                            <button class="btn btn-primary btn-sm mt-2">Acceder</button>
                        </div>
                    </div>
                    <div class="col-md-2">
                        <div class="module-card text-center">
                            <i class="bi bi-pencil-square module-icon"></i>
                            <h5>Jornalización</h5>
                            <button class="btn btn-primary btn-sm mt-2">Acceder</button>
                        </div>
                    </div>
                    <div class="col-md-2">
                        <div class="module-card text-center">
                            <i class="bi bi-file-earmark-spreadsheet module-icon"></i>
                            <h5>Estados Financieros</h5>
                            <button class="btn btn-primary btn-sm mt-2">Acceder</button>
                        </div>
                    </div>
                </div>

                <div id="plan-cuentas-container" style="display: none;" class="mt-4">
                    <div class="d-flex justify-content-between align-items-center mb-3">
                        <h4>Plan de Cuentas</h4>
                        <div>
                            <input type="file" id="excelFileInput" accept=".xlsx, .xls" style="display: none;" onchange="importExcel()">
                            <button class="btn btn-success me-2" onclick="document.getElementById('excelFileInput').click()">
                                <i class="bi bi-file-earmark-excel"></i> Importar Excel
                            </button>
                            <button class="btn btn-success me-2" onclick="exportExcel()">
                                <i class="bi bi-file-earmark-excel"></i> Exportar Excel
                            </button>
                            <button class="btn btn-primary" onclick="agregarCuenta()">
                                <i class="bi bi-plus-circle"></i> Nueva Cuenta
                            </button>
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-md-12">
                            <div class="module-card">
                                <div class="d-flex justify-content-between align-items-center mb-3">
                                    <h4>Plan de Cuentas</h4>
                                    <button class="btn btn-primary" onclick="agregarCuenta()">
                                        <i class="bi bi-plus-circle"></i> Nueva Cuenta
                                    </button>
                                </div>
                                <div class="table-responsive">
                                    <table class="table table-hover custom-table">
                                        <thead>
                                            <tr>
                                                <th>Código</th>
                                                <th>Nombre de Cuenta</th>
                                                <th>Nivel</th>
                                                <th>Tipo</th>
                                                <th>Centro de Costos</th>
                                                <th>Acciones</th>
                                            </tr>
                                        </thead>
                                        <tbody id="cuentas-table-body">
                                            <!-- Nivel 1 -->
                                            <tr class="cuenta-nivel-1">
                                                <td>1</td>
                                                <td>Activos</td>
                                                <td>1</td>
                                                <td>Grupo</td>
                                                <td>
                                                    <span class="badge bg-info">Ventas</span>
                                                    <span class="badge bg-info">Administración</span>
                                                </td>
                                                <td>
                                                    <button class="btn btn-sm btn-primary"><i class="bi bi-pencil"></i></button>
                                                    <button class="btn btn-sm btn-danger"><i class="bi bi-trash"></i></button>
                                                </td>
                                            </tr>
                                            <!-- Nivel 2 -->
                                            <tr class="cuenta-nivel-2">
                                                <td>101</td>
                                                <td>Activos Corrientes</td>
                                                <td>2</td>
                                                <td>Grupo</td>
                                                <td>
                                                    <span class="badge bg-info">Ventas</span>
                                                </td>
                                                <td>
                                                    <button class="btn btn-sm btn-primary"><i class="bi bi-pencil"></i></button>
                                                    <button class="btn btn-sm btn-danger"><i class="bi bi-trash"></i></button>
                                                </td>
                                            </tr>
                                            <!-- Nivel 3 -->
                                            <tr class="cuenta-nivel-3">
                                                <td>10101</td>
                                                <td>Efectivo y Equivalentes</td>
                                                <td>3</td>
                                                <td>Grupo</td>
                                                <td>
                                                    <span class="badge bg-info">Ventas</span>
                                                </td>
                                                <td>
                                                    <button class="btn btn-sm btn-primary"><i class="bi bi-pencil"></i></button>
                                                    <button class="btn btn-sm btn-danger"><i class="bi bi-trash"></i></button>
                                                </td>
                                            </tr>
                                            <!-- Nivel 4 -->
                                            <tr class="cuenta-nivel-4">
                                                <td>1010101</td>
                                                <td>Caja General</td>
                                                <td>4</td>
                                                <td>Grupo</td>
                                                <td>
                                                    <span class="badge bg-info">Ventas</span>
                                                </td>
                                                <td>
                                                    <button class="btn btn-sm btn-primary"><i class="bi bi-pencil"></i></button>
                                                    <button class="btn btn-sm btn-danger"><i class="bi bi-trash"></i></button>
                                                </td>
                                            </tr>
                                            <!-- Nivel 5 -->
                                            <tr class="cuenta-nivel-5">
                                                <td>1010101010</td>
                                                <td>Caja Moneda Nacional</td>
                                                <td>5</td>
                                                <td>Movimiento</td>
                                                <td>
                                                    <span class="badge bg-info">Ventas</span>
                                                </td>
                                                <td>
                                                    <button class="btn btn-sm btn-primary"><i class="bi bi-pencil"></i></button>
                                                    <button class="btn btn-sm btn-danger"><i class="bi bi-trash"></i></button>
                                                </td>
                                            </tr>
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

            </div>

            <!-- Clientes Module -->
            <div id="clientes-module" class="module-content" style="display: none;">
                <div class="row mb-4">
                    <div class="col-md-12">
                        <h2>Gestión de Clientes</h2>
                        <hr>
                    </div>
                </div>

                <div class="row mb-4">
                    <div class="col-md-12">
                        <div class="module-card">
                            <div class="d-flex justify-content-between align-items-center mb-3">
                                <div>
                                    <button class="btn btn-primary me-2" onclick="newClient()">
                                        <i class="bi bi-plus-circle"></i> Nuevo
                                    </button>
                                    <button class="btn btn-warning me-2" onclick="showFilters()">
                                        <i class="bi bi-funnel"></i> Filtrar
                                    </button>
                                    <button class="btn btn-info me-2" onclick="automaticAdjustments()">
                                        <i class="bi bi-gear"></i> Ajustes Automáticos
                                    </button>
                                    <button class="btn btn-secondary" onclick="loadModule('dashboard')">
                                        <i class="bi bi-x-circle"></i> Salir
                                    </button>
                                </div>
                            </div>

                            <div id="filterSection" style="display: none;" class="mb-3">
                                <div class="row">
                                    <div class="col-md-3">
                                        <input type="text" class="form-control" placeholder="NIT">  <!-- Changed from RUC/Tax ID -->
                                    </div>
                                    <div class="col-md-3">
                                        <input type="text" class="form-control" placeholder="Razón Social">
                                    </div>
                                    <div class="col-md-3">
                                        <input type="text" class="form-control" placeholder="Nombre Comercial">
                                    </div>
                                    <div class="col-md-3">
                                        <select class="form-control">
                                            <option value="">Régimen Fiscal</option>
                                            <option>General</option>
                                            <option>Simplificado</option>
                                            <option>Especial</option>
                                        </select>
                                    </div>
                                </div>
                            </div>

                            <div class="table-responsive">
                                <table class="table table-hover custom-table" id="clientsTable">
                                    <thead>
                                        <tr>
                                            <th>NIT</th>  <!-- Changed from Tax ID -->
                                            <th>Razón Social</th>
                                            <th>Nombre Comercial</th>
                                            <th>Dirección</th>
                                            <th>Régimen Fiscal</th>
                                            <th>Cuenta por Cobrar</th>
                                            <th>Cuenta Anticipos</th>
                                            <th>Acciones</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr>
                                            <td>1234567890001</td>
                                            <td>Empresa Ejemplo S.A.</td>
                                            <td>Ejemplo Corp</td>
                                            <td>Calle Principal 123</td>
                                            <td>General</td>
                                            <td>1.1.2.01</td>
                                            <td>2.1.1.01</td>
                                            <td>
                                                <button class="btn btn-sm btn-primary" onclick="editClient(this)">
                                                    <i class="bi bi-pencil"></i>
                                                </button>
                                                <button class="btn btn-sm btn-danger" onclick="deleteClient(this)">
                                                    <i class="bi bi-trash"></i>
                                                </button>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Client Modal -->
            <div class="modal fade" id="clientModal" tabindex="-1">
                <div class="modal-dialog modal-lg">
                    <div class="modal-content">
                        <div class="modal-header">
                            <h5 class="modal-title">Cliente</h5>
                            <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
                        </div>
                        <div class="modal-body">
                            <form id="clientForm">
                                <div class="row mb-3">
                                    <div class="col-md-6">
                                        <label class="form-label">NIT</label>  <!-- Changed from Tax ID -->
                                        <input type="text" class="form-control" id="clientTaxId" required>
                                    </div>
                                    <div class="col-md-6">
                                        <label class="form-label">Régimen Fiscal</label>
                                        <select class="form-control" id="clientTaxRegime" required>
                                            <option value="General">General</option>
                                            <option value="Simplificado">Simplificado</option>
                                            <option value="Especial">Especial</option>
                                            <option value="PequenoContribuyente">Pequeño Contribuyente</option>
                                        </select>
                                    </div>
                                </div>
                                <div class="row mb-3">
                                    <div class="col-md-6">
                                        <label class="form-label">Razón Social</label>
                                        <input type="text" class="form-control" id="clientBusinessName" required>
                                    </div>
                                    <div class="col-md-6">
                                        <label class="form-label">Nombre Comercial</label>
                                        <input type="text" class="form-control" id="clientCommercialName">
                                    </div>
                                </div>
                                <div class="mb-3">
                                    <label class="form-label">Dirección</label>
                                    <textarea class="form-control" id="clientAddress" rows="2" required></textarea>
                                </div>
                                <div class="row mb-3">
                                    <div class="col-md-6">
                                        <label class="form-label">Cuenta por Cobrar</label>
                                        <select class="form-control" id="clientReceivableAccount" required>
                                            <!-- Will be populated dynamically -->
                                        </select>
                                    </div>
                                    <div class="col-md-6">
                                        <label class="form-label">Cuenta Anticipos</label>
                                        <select class="form-control" id="clientAdvanceAccount" required>
                                            <!-- Will be populated dynamically -->
                                        </select>
                                    </div>
                                </div>
                                <div class="mb-3">
                                    <label class="form-label">Clasificación de Pago</label>
                                    <select class="form-control" id="clientPaymentType" onchange="toggleCreditOptions()">
                                        <option value="cash">Contado</option>
                                        <option value="credit">Crédito</option>
                                    </select>
                                </div>
                                <div id="creditOptions" style="display: none;">
                                    <div class="mb-3">
                                        <label class="form-label">Tiempo de Crédito (días)</label>
                                        <input type="number" class="form-control" id="creditDays" min="1" max="360">
                                    </div>
                                    <div class="mb-3">
                                        <label class="form-label">Límite de Crédito</label>
                                        <input type="number" class="form-control" id="creditLimit" min="0" step="0.01">
                                    </div>
                                </div>
                                <div class="tax-configuration mt-3">
                                    <h6>Configuración de Impuestos</h6>
                                    <div class="table-responsive">
                                        <table class="table table-sm">
                                            <thead>
                                                <tr>
                                                    <th>Impuesto</th>
                                                    <th>Porcentaje</th>
                                                    <th>Cuenta Contable</th>
                                                    <th>Activo</th>
                                                </tr>
                                            </thead>
                                            <tbody>
                                                <tr>
                                                    <td>IDP (Impuesto de Petróleo)</td>
                                                    <td><input type="number" class="form-control form-control-sm" id="idpRate" step="0.01"></td>
                                                    <td><select class="form-control form-control-sm" id="idpAccount"></select></td>
                                                    <td><input type="checkbox" class="form-check-input" id="idpActive"></td>
                                                </tr>
                                                <tr>
                                                    <td>TP (Timbre Profesional)</td>
                                                    <td><input type="number" class="form-control form-control-sm" id="tpRate" step="0.01"></td>
                                                    <td><select class="form-control form-control-sm" id="tpAccount"></select></td>
                                                    <td><input type="checkbox" class="form-check-input" id="tpActive"></td>
                                                </tr>
                                                <tr>
                                                    <td>IVA (Impuesto al Valor Agregado)</td>
                                                    <td><input type="number" class="form-control form-control-sm" id="vatRate" step="0.01"></td>
                                                    <td><select class="form-control form-control-sm" id="vatAccount"></select></td>
                                                    <td><input type="checkbox" class="form-check-input" id="vatActive"></td>
                                                </tr>
                                                <tr>
                                                    <td>ISR (Impuesto Sobre la Renta)</td>
                                                    <td><input type="number" class="form-control form-control-sm" id="isrRate" step="0.01"></td>
                                                    <td><select class="form-control form-control-sm" id="isrAccount"></select></td>
                                                    <td><input type="checkbox" class="form-check-input" id="isrActive"></td>
                                                </tr>
                                                <tr>
                                                    <td>TURISMO</td>
                                                    <td><input type="number" class="form-control form-control-sm" id="tourismRate" step="0.01"></td>
                                                    <td><select class="form-control form-control-sm" id="tourismAccount"></select></td>
                                                    <td><input type="checkbox" class="form-check-input" id="tourismActive"></td>
                                                </tr>
                                            </tbody>
                                        </table>
                                    </div>
                                </div>
                            </form>
                        </div>
                        <div class="modal-footer">
                            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                            <button type="button" class="btn btn-primary" onclick="saveClient()">Guardar</button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Inventarios Module -->
            <div id="inventarios-module" class="module-content" style="display: none;">
                <div class="row mb-4">
                    <div class="col-md-12">
                        <h2>Control de Inventario</h2>
                        <hr>
                    </div>
                </div>

                <!-- Inventory Controls -->
                <div class="row mb-4">
                    <div class="col-md-12">
                        <div class="module-card">
                            <div class="d-flex justify-content-between align-items-center mb-3">
                                <div>
                                    <button class="btn btn-primary me-2" onclick="newProduct()">
                                        <i class="bi bi-plus-circle"></i> Nuevo Producto
                                    </button>
                                    <button class="btn btn-warning me-2" onclick="showInventoryFilters()">
                                        <i class="bi bi-funnel"></i> Filtrar
                                    </button>
                                    <button class="btn btn-success me-2" onclick="adjustInventory()">
                                        <i class="bi bi-arrow-repeat"></i> Ajuste de Inventario
                                    </button>
                                    <button class="btn btn-info me-2" onclick="generateInventoryReport()">
                                        <i class="bi bi-file-text"></i> Generar Reporte
                                    </button>
                                    <button class="btn btn-secondary" onclick="loadModule('dashboard')">
                                        <i class="bi bi-x-circle"></i> Salir
                                    </button>
                                </div>
                            </div>

                            <!-- Filters Section -->
                            <div id="inventoryFilterSection" style="display: none;" class="mb-3">
                                <div class="row">
                                    <div class="col-md-3">
                                        <input type="text" class="form-control" placeholder="Código">
                                    </div>
                                    <div class="col-md-3">
                                        <input type="text" class="form-control" placeholder="Descripción">
                                    </div>
                                    <div class="col-md-3">
                                        <select class="form-control">
                                            <option value="">Categoría</option>
                                            <option>Materia Prima</option>
                                            <option>Producto Terminado</option>
                                            <option>Suministros</option>
                                        </select>
                                    </div>
                                    <div class="col-md-3">
                                        <select class="form-control">
                                            <option value="">Estado</option>
                                            <option>Activo</option>
                                            <option>Inactivo</option>
                                        </select>
                                    </div>
                                </div>
                            </div>

                            <!-- Inventory Table -->
                            <div class="table-responsive">
                                <table class="table table-hover custom-table" id="inventoryTable">
                                    <thead>
                                        <tr>
                                            <th>Código</th>
                                            <th>Descripción</th>
                                            <th>Categoría</th>
                                            <th>Unidad</th>
                                            <th>Stock Min.</th>
                                            <th>Stock Máx.</th>
                                            <th>Existencia</th>
                                            <th>Costo Unit.</th>
                                            <th>Cuenta Contable</th>
                                            <th>Estado</th>
                                            <th>Acciones</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr>
                                            <td>P001</td>
                                            <td>Producto Ejemplo 1</td>
                                            <td>Materia Prima</td>
                                            <td>UND</td>
                                            <td>10</td>
                                            <td>100</td>
                                            <td>45</td>
                                            <td>$25.00</td>
                                            <td>1.1.3.01</td>
                                            <td><span class="badge bg-success">Activo</span></td>
                                            <td>
                                                <button class="btn btn-sm btn-primary" onclick="editProduct(this)">
                                                    <i class="bi bi-pencil"></i>
                                                </button>
                                                <button class="btn btn-sm btn-danger" onclick="deleteProduct(this)">
                                                    <i class="bi bi-trash"></i>
                                                </button>
                                                <button class="btn btn-sm btn-info" onclick="showProductHistory(this)">
                                                    <i class="bi bi-clock-history"></i>
                                                </button>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Product Modal -->
            <div class="modal fade" id="productModal" tabindex="-1">
                <div class="modal-dialog modal-lg">
                    <div class="modal-content">
                        <div class="modal-header">
                            <h5 class="modal-title">Producto</h5>
                            <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
                        </div>
                        <div class="modal-body">
                            <form id="productForm">
                                <div class="row mb-3">
                                    <div class="col-md-6">
                                        <label class="form-label">Código</label>
                                        <input type="text" class="form-control" id="productCode" required>
                                    </div>
                                    <div class="col-md-6">
                                        <label class="form-label">Categoría</label>
                                        <select class="form-control" id="productCategory" required>
                                            <option value="Materia Prima">Materia Prima</option>
                                            <option value="Producto Terminado">Producto Terminado</option>
                                            <option value="Suministros">Suministros</option>
                                        </select>
                                    </div>
                                </div>
                                <div class="mb-3">
                                    <label class="form-label">Descripción</label>
                                    <input type="text" class="form-control" id="productDescription" required>
                                </div>
                                <div class="row mb-3">
                                    <div class="col-md-6">
                                        <label class="form-label">Unidad de Medida</label>
                                        <select class="form-control" id="productUnit" required>
                                            <option value="UND">Unidad</option>
                                            <option value="KG">Kilogramo</option>
                                            <option value="LT">Litro</option>
                                            <option value="MT">Metro</option>
                                        </select>
                                    </div>
                                    <div class="col-md-6">
                                        <label class="form-label">Estado</label>
                                        <select class="form-control" id="productStatus" required>
                                            <option value="Activo">Activo</option>
                                            <option value="Inactivo">Inactivo</option>
                                        </select>
                                    </div>
                                </div>
                                <div class="row mb-3">
                                    <div class="col-md-4">
                                        <label class="form-label">Stock Mínimo</label>
                                        <input type="number" class="form-control" id="productMinStock" required min="0">
                                    </div>
                                    <div class="col-md-4">
                                        <label class="form-label">Stock Máximo</label>
                                        <input type="number" class="form-control" id="productMaxStock" required min="0">
                                    </div>
                                    <div class="col-md-4">
                                        <label class="form-label">Costo Unitario</label>
                                        <input type="number" class="form-control" id="productUnitCost" required min="0" step="0.01">
                                    </div>
                                </div>
                                <div class="mb-3">
                                    <label class="form-label">Cuenta Contable</label>
                                    <div id="productAccountContainer">
                                        <!-- Will be replaced with searchable select -->
                                    </div>
                                </div>
                            </form>
                        </div>
                        <div class="modal-footer">
                            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                            <button type="button" class="btn btn-primary" onclick="saveProduct()">Guardar</button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Sales Module -->
            <div id="ventas-module" class="module-content" style="display: none;">
                <div class="row mb-4">
                    <div class="col-md-12">
                        <h2>Facturación</h2>
                        <hr>
                    </div>
                </div>

                <!-- Invoicing Form -->
                <div class="row mb-4">
                    <div class="col-md-12">
                        <div class="module-card">
                            <form id="invoiceForm">
                                <div class="row mb-3">
                                    <div class="col-md-2">
                                        <label class="form-label">Serie</label>
                                        <input type="text" class="form-control" id="invoiceSeries" required>
                                    </div>
                                    <div class="col-md-2">
                                        <label class="form-label">Número</label>
                                        <input type="text" class="form-control" id="invoiceNumber" required>
                                    </div>
                                    <div class="col-md-4">
                                        <label class="form-label">Fecha</label>
                                        <input type="date" class="form-control" id="invoiceDate" required>
                                    </div>
                                    <div class="col-md-4">
                                        <label class="form-label">Condición de Pago</label>
                                        <select class="form-control" id="paymentCondition" required>
                                            <option value="cash">Contado</option>
                                            <option value="credit">Crédito</option>
                                        </select>
                                    </div>
                                </div>

                                <div class="row mb-3">
                                    <div class="col-md-12">
                                        <label class="form-label">Cliente</label>
                                        <div class="input-group">
                                            <input type="text" class="form-control" id="customerSearch" placeholder="Buscar cliente...">
                                            <button class="btn btn-primary" type="button" onclick="searchCustomer()">
                                                <i class="bi bi-search"></i>
                                            </button>
                                        </div>
                                    </div>
                                </div>

                                <div id="customerDetails" class="mb-3" style="display: none;">
                                    <div class="card">
                                        <div class="card-body">
                                            <h6>Detalles del Cliente</h6>
                                            <div class="row">
                                                <div class="col-md-4">
                                                    <strong>NIT:</strong> <span id="customerTaxId"></span>  <!-- Changed label but kept ID for consistency -->
                                                </div>
                                                <div class="col-md-4">
                                                    <strong>Nombre Comercial:</strong> <span id="customerCommercialName"></span>
                                                </div>
                                                <div class="col-md-4">
                                                    <strong>Régimen:</strong> <span id="customerTaxRegime"></span>
                                                </div>
                                            </div>
                                            <div class="row mt-2">
                                                <div class="col-md-12">
                                                    <strong>Dirección:</strong> <span id="customerAddress"></span>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>

                                <div class="row mb-3">
                                    <div class="col-md-12">
                                        <label class="form-label">Producto</label>
                                        <div class="input-group">
                                            <input type="text" class="form-control" id="productSearch" placeholder="Buscar producto...">
                                            <button class="btn btn-primary" type="button" onclick="searchProduct()">
                                                <i class="bi bi-search"></i>
                                            </button>
                                        </div>
                                    </div>
                                </div>

                                <div class="table-responsive mb-3">
                                    <table class="table table-hover" id="invoiceItemsTable">
                                        <thead>
                                            <tr>
                                                <th>Código</th>
                                                <th>Descripción</th>
                                                <th>Cantidad</th>
                                                <th>Precio Unit.</th>
                                                <th>Descuento</th>
                                                <th>Subtotal</th>
                                                <th>Acciones</th>
                                            </tr>
                                        </thead>
                                        <tbody>
                                        </tbody>
                                        <tfoot>
                                            <tr>
                                                <td colspan="5" class="text-end"><strong>Subtotal:</strong></td>
                                                <td><span id="subtotal">0.00</span></td>
                                                <td></td>
                                            </tr>
                                            <tr>
                                                <td colspan="5" class="text-end"><strong>IVA (12%):</strong></td>
                                                <td><span id="iva">0.00</span></td>
                                                <td></td>
                                            </tr>
                                            <tr>
                                                <td colspan="5" class="text-end"><strong>Total:</strong></td>
                                                <td><span id="total">0.00</span></td>
                                                <td></td>
                                            </tr>
                                        </tfoot>
                                    </table>
                                </div>

                                <div class="row">
                                    <div class="col-md-12 text-end">
                                        <button type="button" class="btn btn-secondary" onclick="loadModule('dashboard')">Cancelar</button>
                                        <button type="button" class="btn btn-primary" onclick="saveInvoice()">Guardar</button>
                                        <button type="button" class="btn btn-success" onclick="printInvoice()">Imprimir</button>
                                    </div>
                                </div>
                            </form>
                        </div>
                    </div>
                </div>
            </div>

        </div>
    </div>
</div>

<!-- Loading Overlay -->
<div class="loading-overlay" style="display: none;">
    <div class="spinner"></div>
</div>

<script>
// Initialize Charts
document.addEventListener('DOMContentLoaded', function() {
    // Sales Chart
    const salesCtx = document.getElementById('salesChart').getContext('2d');
    new Chart(salesCtx, {
        type: 'line',
        data: {
            labels: ['Ene', 'Feb', 'Mar', 'Abr', 'May', 'Jun'],
            datasets: [{
                label: 'Ventas 2023',
                data: [65, 59, 80, 81, 56, 55],
                borderColor: '#3498db',
                tension: 0.1,
                fill: false
            }]
        },
        options: {
            responsive: true,
            plugins: {
                legend: {
                    position: 'top',
                }
            }
        }
    });

    // Income Distribution Chart
    const incomeCtx = document.getElementById('incomeChart').getContext('2d');
    new Chart(incomeCtx, {
        type: 'doughnut',
        data: {
            labels: ['Ventas', 'Servicios', 'Otros'],
            datasets: [{
                data: [300, 150, 100],
                backgroundColor: ['#2ecc71', '#3498db', '#e74c3c']
            }]
        },
        options: {
            responsive: true,
            plugins: {
                legend: {
                    position: 'top',
                }
            }
        }
    });
});

// Navigation Handler
document.querySelectorAll('.nav-link').forEach(link => {
    link.addEventListener('click', function(e) {
        e.preventDefault();
        const module = this.getAttribute('href').substring(1);
        // Reset active state
        document.querySelectorAll('.nav-link').forEach(navLink => {
            navLink.classList.remove('active');
        });
        this.classList.add('active');
        loadModule(module);
    });
});

// Modify the existing click handler for the Plan de Cuentas button
document.querySelector('#contabilidad-module .btn').addEventListener('click', function() {
    if (this.parentElement.querySelector('h5').textContent === 'Plan de Cuentas') {
        document.getElementById('plan-cuentas-container').style.display = 'block';
    }
});

// Module Loading Function
function loadModule(moduleName) {
    const loadingOverlay = document.querySelector('.loading-overlay');
    loadingOverlay.style.display = 'flex';

    // Hide all content sections first
    const mainContent = document.querySelectorAll('.main-content > .row:not(.module-content)');
    const moduleContents = document.querySelectorAll('.module-content');
    
    // Hide main dashboard content
    mainContent.forEach(content => {
        content.style.display = 'none';
    });
    
    // Hide all module contents
    moduleContents.forEach(content => {
        content.style.display = 'none';
    });

    // Show specific module or dashboard
    if (moduleName === 'dashboard') {
        mainContent.forEach(content => {
            content.style.display = 'block';
        });
    } else {
        const targetModule = document.getElementById(`${moduleName}-module`);
        if (targetModule) {
            targetModule.style.display = 'block';
            
            // If loading ventas module, set today's date
            if (moduleName === 'ventas') {
                const today = new Date().toISOString().split('T')[0];
                document.getElementById('invoiceDate').value = today;
            }
        }
    }

    setTimeout(() => {
        loadingOverlay.style.display = 'none';
        console.log(`Loading module: ${moduleName}`);
    }, 1000);
}

// Add new account function
function agregarCuenta() {
    const modal = new bootstrap.Modal(document.getElementById('nuevaCuentaModal'));
    modal.show();
}

// User Authentication
class Auth {
    static checkAuth() {
        // Implementation for checking user authentication
        return true;
    }

    static login(username, password) {
        // Implementation for user login
        return true;
    }

    static logout() {
        // Implementation for user logout
        return true;
    }
}

// Data Management
class DataManager {
    static async fetchData(endpoint) {
        // Implementation for fetching data
        return {};
    }

    static async saveData(endpoint, data) {
        // Implementation for saving data
        return true;
    }
}

// Function to export to Excel
function exportExcel() {
    // Show loading overlay
    document.querySelector('.loading-overlay').style.display = 'flex';
    
    const rows = Array.from(document.querySelectorAll('#cuentas-table-body tr')).map(row => ({
        codigo: row.cells[0].textContent,
        nombre: row.cells[1].textContent,
        nivel: row.cells[2].textContent,
        tipo: row.cells[3].textContent,
        centroCostos: row.cells[4].textContent
    }));

    // Create worksheet
    const worksheet = XLSX.utils.json_to_sheet(rows);
    const workbook = XLSX.utils.book_new();
    XLSX.utils.book_append_sheet(workbook, worksheet, "Plan de Cuentas");
    
    // Save file
    XLSX.writeFile(workbook, "plan_de_cuentas.xlsx");
    
    // Hide loading overlay
    setTimeout(() => {
        document.querySelector('.loading-overlay').style.display = 'none';
    }, 1000);
}

// Function to import from Excel
function importExcel() {
    const file = document.getElementById('excelFileInput').files[0];
    const reader = new FileReader();
    
    // Show loading overlay
    document.querySelector('.loading-overlay').style.display = 'flex';

    reader.onload = function(e) {
        const data = new Uint8Array(e.target.result);
        const workbook = XLSX.read(data, { type: 'array' });
        
        // Get first worksheet
        const worksheet = workbook.Sheets[workbook.SheetNames[0]];
        const jsonData = XLSX.utils.sheet_to_json(worksheet);

        // Clear existing table
        const tbody = document.getElementById('cuentas-table-body');
        tbody.innerHTML = '';

        // Add imported data
        jsonData.forEach(row => {
            const newRow = `
                <tr class="cuenta-nivel-${row.nivel}">
                    <td>${row.codigo}</td>
                    <td>${row.nombre}</td>
                    <td>${row.nivel}</td>
                    <td>${row.tipo}</td>
                    <td>
                        <span class="badge bg-info">${row.centroCostos}</span>
                    </td>
                    <td>
                        <button class="btn btn-sm btn-primary"><i class="bi bi-pencil"></i></button>
                        <button class="btn btn-sm btn-danger"><i class="bi bi-trash"></i></button>
                    </td>
                </tr>
            `;
            tbody.insertAdjacentHTML('beforeend', newRow);
        });

        // Hide loading overlay
        document.querySelector('.loading-overlay').style.display = 'none';
    };

    reader.readAsArrayBuffer(file);
}

// Cost Center Management Modals
const costCenterModalHTML = `
<div class="modal fade" id="costCenterModal" tabindex="-1">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title">Gestión de Centros de Costos</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
            </div>
            <div class="modal-body">
                <div class="mb-3">
                    <button class="btn btn-primary btn-sm" onclick="addNewCostCenter()">
                        <i class="bi bi-plus-circle"></i> Nuevo Centro de Costos
                    </button>
                </div>
                <div class="table-responsive">
                    <table class="table table-hover" id="costCenterTable">
                        <thead>
                            <tr>
                                <th>Código</th>
                                <th>Nombre</th>
                                <th>Estado</th>
                                <th>Acciones</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>CC001</td>
                                <td>Ventas</td>
                                <td><span class="badge bg-success">Activo</span></td>
                                <td>
                                    <button class="btn btn-sm btn-primary" onclick="editCostCenter(this)">
                                        <i class="bi bi-pencil"></i>
                                    </button>
                                    <button class="btn btn-sm btn-danger" onclick="deleteCostCenter(this)">
                                        <i class="bi bi-trash"></i>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td>CC002</td>
                                <td>Administración</td>
                                <td><span class="badge bg-success">Activo</span></td>
                                <td>
                                    <button class="btn btn-sm btn-primary" onclick="editCostCenter(this)">
                                        <i class="bi bi-pencil"></i>
                                    </button>
                                    <button class="btn btn-sm btn-danger" onclick="deleteCostCenter(this)">
                                        <i class="bi bi-trash"></i>
                                    </button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
</div>

<div class="modal fade" id="costCenterEditModal" tabindex="-1">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title">Editar Centro de Costos</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
            </div>
            <div class="modal-body">
                <form id="costCenterForm">
                    <div class="mb-3">
                        <label class="form-label">Código</label>
                        <input type="text" class="form-control" id="costCenterCode">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Nombre</label>
                        <input type="text" class="form-control" id="costCenterName">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Estado</label>
                        <select class="form-control" id="costCenterStatus">
                            <option value="active">Activo</option>
                            <option value="inactive">Inactivo</option>
                        </select>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                <button type="button" class="btn btn-primary" onclick="saveCostCenter()">Guardar</button>
            </div>
        </div>
    </div>
</div>
`;

document.body.insertAdjacentHTML('beforeend', costCenterModalHTML);

// Cost Center Management Functions
function manageCostCenters() {
    const modal = new bootstrap.Modal(document.getElementById('costCenterModal'));
    modal.show();
    updateAccountCostCenters(); // Update cost centers in account modal when managing them
}

function addNewCostCenter() {
    const editModal = new bootstrap.Modal(document.getElementById('costCenterEditModal'));
    document.getElementById('costCenterCode').value = '';
    document.getElementById('costCenterName').value = '';
    document.getElementById('costCenterStatus').value = 'active';
    editModal.show();
}

function editCostCenter(button) {
    const row = button.closest('tr');
    const code = row.cells[0].textContent;
    const name = row.cells[1].textContent;
    const status = row.cells[2].querySelector('.badge').textContent === 'Activo' ? 'active' : 'inactive';

    const editModal = new bootstrap.Modal(document.getElementById('costCenterEditModal'));
    document.getElementById('costCenterCode').value = code;
    document.getElementById('costCenterName').value = name;
    document.getElementById('costCenterStatus').value = status;
    editModal.show();
}

function deleteCostCenter(button) {
    if (confirm('¿Está seguro de que desea eliminar este centro de costos?')) {
        button.closest('tr').remove();
    }
}

function saveCostCenter() {
    const code = document.getElementById('costCenterCode').value;
    const name = document.getElementById('costCenterName').value;
    const status = document.getElementById('costCenterStatus').value;

    const newRow = `
        <tr>
            <td>${code}</td>
            <td>${name}</td>
            <td><span class="badge bg-${status === 'active' ? 'success' : 'danger'}">${status === 'active' ? 'Activo' : 'Inactivo'}</span></td>
            <td>
                <button class="btn btn-sm btn-primary" onclick="editCostCenter(this)">
                    <i class="bi bi-pencil"></i>
                </button>
                <button class="btn btn-sm btn-danger" onclick="deleteCostCenter(this)">
                    <i class="bi bi-trash"></i>
                </button>
            </td>
        </tr>
    `;

    const tbody = document.getElementById('costCenterTable').querySelector('tbody');
    tbody.insertAdjacentHTML('beforeend', newRow);

    const editModal = bootstrap.Modal.getInstance(document.getElementById('costCenterEditModal'));
    editModal.hide();
}

// New Account Modal HTML
const accountModalHTML = `
<div class="modal fade" id="nuevaCuentaModal" tabindex="-1">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title">Nueva Cuenta</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
            </div>
            <div class="modal-body">
                <form id="accountForm">
                    <div class="mb-3">
                        <label class="form-label">Código</label>
                        <input type="text" class="form-control" id="accountCode" required>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Nombre</label>
                        <input type="text" class="form-control" id="accountName" required>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Nivel</label>
                        <select class="form-control" id="accountLevel" required>
                            <option value="1">Nivel 1</option>
                            <option value="2">Nivel 2</option>
                            <option value="3">Nivel 3</option>
                            <option value="4">Nivel 4</option>
                            <option value="5">Nivel 5</option>
                        </select>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Tipo</label>
                        <select class="form-control" id="accountType" required>
                            <option value="Grupo">Grupo</option>
                            <option value="Movimiento">Movimiento</option>
                        </select>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Centros de Costos</label>
                        <select class="form-control" id="accountCostCenters" multiple>
                            <!-- Cost centers will be populated dynamically -->
                        </select>
                        <small class="text-muted">Mantenga presionado Ctrl para seleccionar múltiples centros de costos</small>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                <button type="button" class="btn btn-primary" onclick="saveAccount()">Guardar</button>
            </div>
        </div>
    </div>
</div>
`;

document.body.insertAdjacentHTML('beforeend', accountModalHTML);

// Function to handle account creation/editing
function saveAccount() {
    const code = document.getElementById('accountCode').value;
    const name = document.getElementById('accountName').value;
    const level = document.getElementById('accountLevel').value;
    const type = document.getElementById('accountType').value;
    const costCenters = Array.from(document.getElementById('accountCostCenters').selectedOptions)
        .map(option => option.text);

    const costCenterBadges = costCenters
        .map(cc => `<span class="badge bg-info me-1">${cc}</span>`)
        .join('');

    const newRow = `
        <tr class="cuenta-nivel-${level}">
            <td>${code}</td>
            <td>${name}</td>
            <td>${level}</td>
            <td>${type}</td>
            <td>${costCenterBadges}</td>
            <td>
                <button class="btn btn-sm btn-primary" onclick="editAccount(this)">
                    <i class="bi bi-pencil"></i>
                </button>
                <button class="btn btn-sm btn-danger" onclick="deleteAccount(this)">
                    <i class="bi bi-trash"></i>
                </button>
            </td>
        </tr>
    `;

    const tbody = document.getElementById('cuentas-table-body');
    tbody.insertAdjacentHTML('beforeend', newRow);

    const modal = bootstrap.Modal.getInstance(document.getElementById('nuevaCuentaModal'));
    modal.hide();
}

// Function to update cost centers in the account modal
function updateAccountCostCenters() {
    const costCenters = Array.from(document.querySelectorAll('#costCenterTable tbody tr'))
        .map(row => ({
            code: row.cells[0].textContent,
            name: row.cells[1].textContent,
            status: row.cells[2].querySelector('.badge').textContent
        }))
        .filter(cc => cc.status === 'Activo');

    const select = document.getElementById('accountCostCenters');
    select.innerHTML = costCenters.map(cc => 
        `<option value="${cc.code}">${cc.name}</option>`
    ).join('');
}

// Function to edit an account
function editAccount(button) {
    const row = button.closest('tr');
    const code = row.cells[0].textContent;
    const name = row.cells[1].textContent;
    const level = row.cells[2].textContent;
    const type = row.cells[3].textContent;
    const costCenters = Array.from(row.cells[4].querySelectorAll('.badge'))
        .map(badge => badge.textContent);

    document.getElementById('accountCode').value = code;
    document.getElementById('accountName').value = name;
    document.getElementById('accountLevel').value = level;
    document.getElementById('accountType').value = type;

    const costCenterSelect = document.getElementById('accountCostCenters');
    Array.from(costCenterSelect.options).forEach(option => {
        option.selected = costCenters.includes(option.text);
    });

    const modal = new bootstrap.Modal(document.getElementById('nuevaCuentaModal'));
    modal.show();
}

// Function to show filters
function showFilters() {
    const filterSection = document.getElementById('filterSection');
    filterSection.style.display = filterSection.style.display === 'none' ? 'block' : 'none';
}

// Function to create a new client
function newClient() {
    // Clear form
    document.getElementById('clientForm').reset();
    // Populate account dropdowns
    populateAccountDropdowns();
    // Show modal
    const modal = new bootstrap.Modal(document.getElementById('clientModal'));
    modal.show();
}

// Function to edit a client
function editClient(button) {
    const row = button.closest('tr');
    const cells = row.cells;
    
    // Fill form with client data
    document.getElementById('clientTaxId').value = cells[0].textContent;  // Changed from Tax ID
    document.getElementById('clientBusinessName').value = cells[1].textContent;
    document.getElementById('clientCommercialName').value = cells[2].textContent;
    document.getElementById('clientAddress').value = cells[3].textContent;
    document.getElementById('clientTaxRegime').value = cells[4].textContent;
    
    // Populate and set account dropdowns
    populateAccountDropdowns();
    document.getElementById('clientReceivableAccount').value = cells[5].textContent;
    document.getElementById('clientAdvanceAccount').value = cells[6].textContent;

    // Extract credit info from the business name cell
    const creditInfo = cells[1].querySelector('small');
    if (creditInfo && creditInfo.textContent.includes('Crédito')) {
        document.getElementById('clientPaymentType').value = 'credit';
        const creditMatch = creditInfo.textContent.match(/Crédito: (\d+) días \/ Límite: \$(\d+(?:\.\d{2})?)/);
        if (creditMatch) {
            document.getElementById('creditDays').value = creditMatch[1];
            document.getElementById('creditLimit').value = creditMatch[2];
        }
        toggleCreditOptions();
    } else {
        document.getElementById('clientPaymentType').value = 'cash';
        document.getElementById('creditDays').value = '';
        document.getElementById('creditLimit').value = '';
        toggleCreditOptions();
    }
    
    // Show modal
    const modal = new bootstrap.Modal(document.getElementById('clientModal'));
    modal.show();
}

// Function to delete a client
function deleteClient(button) {
    if (confirm('¿Está seguro de que desea eliminar este cliente?')) {
        button.closest('tr').remove();
    }
}

// Function to save a client
function saveClient() {
    const form = document.getElementById('clientForm');
    if (!form.checkValidity()) {
        form.reportValidity();
        return;
    }
    
    const nit = document.getElementById('clientTaxId').value;
    
    // Check for duplicate NIT
    const existingClients = Array.from(document.querySelectorAll('#clientsTable tbody tr')).map(row => ({
        nit: row.cells[0].textContent
    }));
    
    if (existingClients.some(client => client.nit === nit)) {
        alert('Ya existe un cliente con este NIT. No se permiten duplicados.');
        return;
    }
    
    const getValue = (elementId) => {
        const element = document.getElementById(elementId);
        const value = element.value;
        return value.split(' - ')[0]; // Extract account code from the display value
    };

    const clientData = {
        nit: nit,
        businessName: document.getElementById('clientBusinessName').value,
        commercialName: document.getElementById('clientCommercialName').value,
        address: document.getElementById('clientAddress').value,
        taxRegime: document.getElementById('clientTaxRegime').value,
        receivableAccount: getValue('clientReceivableAccount'),
        advanceAccount: getValue('clientAdvanceAccount'),
        paymentType: document.getElementById('clientPaymentType').value,
        creditDays: document.getElementById('creditDays').value,
        creditLimit: document.getElementById('creditLimit').value,
        taxConfiguration: {
            idp: {
                rate: document.getElementById('idpRate').value,
                account: getValue('idpAccount'),
                active: document.getElementById('idpActive').checked
            },
            tp: {
                rate: document.getElementById('tpRate').value,
                account: getValue('tpAccount'),
                active: document.getElementById('tpActive').checked
            },
            vat: {
                rate: document.getElementById('vatRate').value,
                account: getValue('vatAccount'),
                active: document.getElementById('vatActive').checked
            },
            isr: {
                rate: document.getElementById('isrRate').value,
                account: getValue('isrAccount'),
                active: document.getElementById('isrActive').checked
            },
            tourism: {
                rate: document.getElementById('tourismRate').value,
                account: getValue('tourismAccount'),
                active: document.getElementById('tourismActive').checked
            }
        }
    };

    const newRow = `
        <tr>
            <td>${clientData.nit}</td>
            <td>${clientData.businessName}</td>
            <td>${clientData.commercialName}</td>
            <td>${clientData.address}</td>
            <td>${clientData.taxRegime}</td>
            <td>${clientData.receivableAccount}</td>
            <td>${clientData.advanceAccount}</td>
            <td>
                <button class="btn btn-sm btn-primary" onclick="editClient(this)">
                    <i class="bi bi-pencil"></i>
                </button>
                <button class="btn btn-sm btn-danger" onclick="deleteClient(this)">
                    <i class="bi bi-trash"></i>
                </button>
            </td>
        </tr>
    `;
    
    document.querySelector('#clientsTable tbody').insertAdjacentHTML('beforeend', newRow);
    
    const modal = bootstrap.Modal.getInstance(document.getElementById('clientModal'));
    modal.hide();
}

// Function to populate account dropdowns in the client modal
function populateAccountDropdowns() {
    // Get accounts from chart of accounts table
    const accountsTable = document.getElementById('cuentas-table-body');
    const allAccounts = Array.from(accountsTable.querySelectorAll('tr')).map(row => ({
        code: row.cells[0].textContent,
        name: row.cells[1].textContent,
        type: row.cells[3].textContent
    })).filter(acc => acc.type === 'Movimiento'); // Only movement accounts can be selected

    // Update the select elements to include search functionality
    const accountSelects = [
        'clientReceivableAccount', 
        'clientAdvanceAccount',
        'idpAccount',
        'tpAccount',
        'vatAccount',
        'isrAccount',
        'tourismAccount'
    ];

    accountSelects.forEach(selectId => {
        const currentSelect = document.getElementById(selectId);
        const searchableSelect = createSearchableSelect(currentSelect, allAccounts);
        currentSelect.parentNode.replaceChild(searchableSelect, currentSelect);
    });
}

function createSearchableSelect(originalSelect, accounts) {
    const container = document.createElement('div');
    container.className = 'position-relative';
    
    const input = document.createElement('input');
    input.type = 'text';
    input.className = 'form-control form-control-sm';
    input.placeholder = 'Buscar cuenta...';
    input.id = originalSelect.id;
    input.setAttribute('list', `${originalSelect.id}-list`);

    const datalist = document.createElement('datalist');
    datalist.id = `${originalSelect.id}-list`;

    accounts.forEach(account => {
        const option = document.createElement('option');
        option.value = `${account.code} - ${account.name}`;
        option.setAttribute('data-code', account.code);
        datalist.appendChild(option);
    });

    container.appendChild(input);
    container.appendChild(datalist);

    // Add validation event
    input.addEventListener('change', function() {
        const selectedValue = this.value;
        const isValid = accounts.some(acc => 
            `${acc.code} - ${acc.name}` === selectedValue
        );
        
        if (!isValid) {
            this.value = '';
            alert('Por favor seleccione una cuenta válida del listado');
        }
    });

    return container;
}

// Function for automatic adjustments
function automaticAdjustments() {
    alert('Iniciando proceso de ajustes automáticos...');
    // Implement automatic adjustments logic here
}

// Function to handle tax regime change
document.getElementById('clientTaxRegime').addEventListener('change', function() {
    const regime = this.value;
    setDefaultTaxConfiguration(regime);
});

// Function to set default tax configuration based on regime
function setDefaultTaxConfiguration(regime) {
    clearTaxConfiguration();
    
    switch(regime) {
        case 'General':
            setTaxValues({
                idp: { rate: 0.10, active: true },
                tp: { rate: 0.03, active: true },
                vat: { rate: 0.12, active: true },
                isr: { rate: 0.25, active: true },
                tourism: { rate: 0.05, active: false }
            });
            break;
            
        case 'Simplificado':
            setTaxValues({
                idp: { rate: 0.05, active: true },
                tp: { rate: 0.02, active: true },
                vat: { rate: 0.12, active: true },
                isr: { rate: 0.07, active: true },
                tourism: { rate: 0.03, active: false }
            });
            break;
            
        case 'Especial':
            setTaxValues({
                idp: { rate: 0.15, active: true },
                tp: { rate: 0.04, active: true },
                vat: { rate: 0.12, active: true },
                isr: { rate: 0.31, active: true },
                tourism: { rate: 0.07, active: true }
            });
            break;
            
        case 'PequenoContribuyente':
            setTaxValues({
                idp: { rate: 0.05, active: false },
                tp: { rate: 0.01, active: true },
                vat: { rate: 0.05, active: true },
                isr: { rate: 0.05, active: true },
                tourism: { rate: 0, active: false }
            });
            break;
    }
}

// Function to clear all tax configurations
function clearTaxConfiguration() {
    const taxes = ['idp', 'tp', 'vat', 'isr', 'tourism'];
    taxes.forEach(tax => {
        document.getElementById(`${tax}Rate`).value = '';
        document.getElementById(`${tax}Active`).checked = false;
    });
}

// Function to set tax values
function setTaxValues(config) {
    for (const [tax, values] of Object.entries(config)) {
        document.getElementById(`${tax}Rate`).value = values.rate;
        document.getElementById(`${tax}Active`).checked = values.active;
    }
}

// Function to toggle credit options visibility
function toggleCreditOptions() {
    const paymentType = document.getElementById('clientPaymentType').value;
    const creditOptions = document.getElementById('creditOptions');
    creditOptions.style.display = paymentType === 'credit' ? 'block' : 'none';
}

// Show Inventory Filters
function showInventoryFilters() {
const filterSection = document.getElementById('inventoryFilterSection');
    filterSection.style.display = filterSection.style.display === 'none' ? 'block' : 'none';
}

// New Product
function newProduct() {
    document.getElementById('productForm').reset();
    const accountContainer = document.getElementById('productAccountContainer');
    const accountsTable = document.getElementById('cuentas-table-body');
    const allAccounts = Array.from(accountsTable.querySelectorAll('tr'))
        .map(row => ({
            code: row.cells[0].textContent,
            name: row.cells[1].textContent,
            type: row.cells[3].textContent
        }))
        .filter(acc => acc.type === 'Movimiento');

    const searchableSelect = createSearchableSelect(
        document.createElement('select'),
        allAccounts
    );
    searchableSelect.id = 'productAccount';
    accountContainer.innerHTML = '';
    accountContainer.appendChild(searchableSelect);

    const modal = new bootstrap.Modal(document.getElementById('productModal'));
    modal.show();
}

// Edit Product
function editProduct(button) {
    const row = button.closest('tr');
    const cells = row.cells;

    document.getElementById('productCode').value = cells[0].textContent;
    document.getElementById('productDescription').value = cells[1].textContent;
    document.getElementById('productCategory').value = cells[2].textContent;
    document.getElementById('productUnit').value = cells[3].textContent;
    document.getElementById('productMinStock').value = cells[4].textContent;
    document.getElementById('productMaxStock').value = cells[5].textContent;
    document.getElementById('productUnitCost').value = cells[7].textContent.replace('$', '');
    
    const accountInput = document.querySelector('#productAccountContainer input');
    if (accountInput) {
        accountInput.value = `${cells[8].textContent} - Cuenta Inventario`;
    }
    
    document.getElementById('productStatus').value = 
        cells[9].querySelector('.badge').textContent;

    const modal = new bootstrap.Modal(document.getElementById('productModal'));
    modal.show();
}

// Delete Product
function deleteProduct(button) {
    if (confirm('¿Está seguro de que desea eliminar este producto?')) {
        button.closest('tr').remove();
    }
}

// Save Product
function saveProduct() {
    const form = document.getElementById('productForm');
    if (!form.checkValidity()) {
        form.reportValidity();
        return;
    }

    const productData = {
        code: document.getElementById('productCode').value,
        description: document.getElementById('productDescription').value,
        category: document.getElementById('productCategory').value,
        unit: document.getElementById('productUnit').value,
        minStock: document.getElementById('productMinStock').value,
        maxStock: document.getElementById('productMaxStock').value,
        unitCost: document.getElementById('productUnitCost').value,
        account: document.querySelector('#productAccountContainer input').value.split(' - ')[0],
        status: document.getElementById('productStatus').value
    };

    const newRow = `
        <tr>
            <td>${productData.code}</td>
            <td>${productData.description}</td>
            <td>${productData.category}</td>
            <td>${productData.unit}</td>
            <td>${productData.minStock}</td>
            <td>${productData.maxStock}</td>
            <td>0</td>
            <td>$${parseFloat(productData.unitCost).toFixed(2)}</td>
            <td>${productData.account}</td>
            <td><span class="badge bg-${productData.status === 'Activo' ? 'success' : 'danger'}">${productData.status}</span></td>
            <td>
                <button class="btn btn-sm btn-primary" onclick="editProduct(this)">
                    <i class="bi bi-pencil"></i>
                </button>
                <button class="btn btn-sm btn-danger" onclick="deleteProduct(this)">
                    <i class="bi bi-trash"></i>
                </button>
                <button class="btn btn-sm btn-info" onclick="showProductHistory(this)">
                    <i class="bi bi-clock-history"></i>
                </button>
            </td>
        </tr>
    `;

    document.querySelector('#inventoryTable tbody').insertAdjacentHTML('beforeend', newRow);
    
    const modal = bootstrap.Modal.getInstance(document.getElementById('productModal'));
    modal.hide();
}

// Invoice Management Functions
function searchCustomer() {
    const searchTerm = document.getElementById('customerSearch').value;
    
    // Simulated customer search - In real implementation, this would query your database
    const customersTable = document.querySelector('#clientsTable tbody');
    const customers = Array.from(customersTable.querySelectorAll('tr')).map(row => ({
        nit: row.cells[0].textContent,  // Changed property name for clarity
        businessName: row.cells[1].textContent.split('<br>')[0],
        commercialName: row.cells[2].textContent,
        address: row.cells[3].textContent,
        taxRegime: row.cells[4].textContent
    }));

    const customer = customers.find(c => 
        c.nit.includes(searchTerm) ||  // Updated reference
        c.businessName.toLowerCase().includes(searchTerm.toLowerCase())
    );

    if (customer) {
        document.getElementById('customerDetails').style.display = 'block';
        document.getElementById('customerTaxId').textContent = customer.nit;  // Changed from Tax ID
        document.getElementById('customerCommercialName').textContent = customer.commercialName;
        document.getElementById('customerTaxRegime').textContent = customer.taxRegime;
        document.getElementById('customerAddress').textContent = customer.address;
    } else {
        alert('Cliente no encontrado');
    }
}

function searchProduct() {
    const searchTerm = document.getElementById('productSearch').value;
    
    // Simulated product search
    const productsTable = document.querySelector('#inventoryTable tbody');
    const products = Array.from(productsTable.querySelectorAll('tr')).map(row => ({
        code: row.cells[0].textContent,
        description: row.cells[1].textContent,
        unitCost: parseFloat(row.cells[7].textContent.replace('$', '')),
        stock: parseInt(row.cells[6].textContent)
    }));

    const product = products.find(p => 
        p.code.includes(searchTerm) || 
        p.description.toLowerCase().includes(searchTerm.toLowerCase())
    );

    if (product) {
        addProductToInvoice(product);
    } else {
        alert('Producto no encontrado');
    }
}

function addProductToInvoice(product) {
    const tbody = document.querySelector('#invoiceItemsTable tbody');
    const quantity = 1;
    const discount = 0;
    const subtotal = quantity * product.unitCost * (1 - discount / 100);

    const newRow = `
        <tr>
            <td>${product.code}</td>
            <td>${product.description}</td>
            <td>
                <input type="number" class="form-control form-control-sm quantity-input" 
                       value="${quantity}" min="1" max="${product.stock}" 
                       onchange="updateInvoiceTotals()">
            </td>
            <td>
                <input type="number" class="form-control form-control-sm price-input" 
                       value="${product.unitCost}" step="0.01" min="0" 
                       onchange="updateInvoiceTotals()">
            </td>
            <td>
                <input type="number" class="form-control form-control-sm discount-input" 
                       value="${discount}" min="0" max="100" 
                       onchange="updateInvoiceTotals()">
            </td>
            <td class="subtotal">${subtotal.toFixed(2)}</td>
            <td>
                <button type="button" class="btn btn-sm btn-danger" onclick="removeInvoiceItem(this)">
                    <i class="bi bi-trash"></i>
                </button>
            </td>
        </tr>
    `;

    tbody.insertAdjacentHTML('beforeend', newRow);
    updateInvoiceTotals();
    document.getElementById('productSearch').value = '';
}

function removeInvoiceItem(button) {
    button.closest('tr').remove();
    updateInvoiceTotals();
}

function updateInvoiceTotals() {
    const rows = document.querySelectorAll('#invoiceItemsTable tbody tr');
    let subtotal = 0;

    rows.forEach(row => {
        const quantity = parseFloat(row.querySelector('.quantity-input').value);
        const price = parseFloat(row.querySelector('.price-input').value);
        const discount = parseFloat(row.querySelector('.discount-input').value);
        const rowSubtotal = quantity * price * (1 - discount / 100);
        row.querySelector('.subtotal').textContent = rowSubtotal.toFixed(2);
        subtotal += rowSubtotal;
    });

    const iva = subtotal * 0.12;
    const total = subtotal + iva;

    document.getElementById('subtotal').textContent = subtotal.toFixed(2);
    document.getElementById('iva').textContent = iva.toFixed(2);
    document.getElementById('total').textContent = total.toFixed(2);
}

function saveInvoice() {
    // Validate required fields
    const form = document.getElementById('invoiceForm');
    if (!form.checkValidity()) {
        form.reportValidity();
        return;
    }

    // Validate customer selection
    if (document.getElementById('customerDetails').style.display === 'none') {
        alert('Por favor seleccione un cliente');
        return;
    }

    // Validate items
    const items = document.querySelectorAll('#invoiceItemsTable tbody tr');
    if (items.length === 0) {
        alert('Por favor agregue al menos un producto');
        return;
    }

    alert('Factura guardada exitosamente');
    form.reset();
    document.getElementById('customerDetails').style.display = 'none';
    document.querySelector('#invoiceItemsTable tbody').innerHTML = '';
    updateInvoiceTotals();
}

function printInvoice() {
    // Create print modal if it doesn't exist
    if (!document.getElementById('printInvoiceModal')) {
        const modalHTML = `
            <div class="modal fade" id="printInvoiceModal" tabindex="-1">
                <div class="modal-dialog modal-xl">
                    <div class="modal-content">
                        <div class="modal-header">
                            <h5 class="modal-title">Personalizar Formato de Factura</h5>
                            <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
                        </div>
                        <div class="modal-body">
                            <div class="row mb-3">
                                <div class="col-md-12">
                                    <div class="card">
                                        <div class="card-body">
                                            <h6>Configuración del Formato</h6>
                                            <div class="row">
                                                <div class="col-md-6">
                                                    <div class="mb-3">
                                                        <label class="form-label">Logo de la Empresa</label>
                                                        <input type="file" class="form-control" id="companyLogo" accept="image/*">
                                                    </div>
                                                    <div class="mb-3">
                                                        <label class="form-label">Nombre de la Empresa</label>
                                                        <input type="text" class="form-control" id="companyName" value="Mi Empresa, S.A.">
                                                    </div>
                                                    <div class="mb-3">
                                                        <label class="form-label">Dirección</label>
                                                        <textarea class="form-control" id="companyAddress">Dirección de la empresa</textarea>
                                                    </div>
                                                    <div class="mb-3">
                                                        <label class="form-label">Información Adicional</label>
                                                        <textarea class="form-control" id="additionalInfo">Tel: (502) 2222-2222</textarea>
                                                    </div>
                                                </div>
                                                <div class="col-md-6">
                                                    <div class="mb-3">
                                                        <label class="form-label">Color Principal</label>
                                                        <input type="color" class="form-control" id="primaryColor" value="#2c3e50">
                                                    </div>
                                                    <div class="mb-3">
                                                        <label class="form-label">Fuente</label>
                                                        <select class="form-control" id="fontFamily">
                                                            <option value="Arial">Arial</option>
                                                            <option value="Times New Roman">Times New Roman</option>
                                                            <option value="Courier New">Courier New</option>
                                                        </select>
                                                    </div>
                                                    <div class="mb-3">
                                                        <label class="form-label">Texto del Pie de Página</label>
                                                        <textarea class="form-control" id="footerText">Gracias por su preferencia</textarea>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            
                            <div id="printInvoice">
                                <!-- Invoice content will be generated here -->
                            </div>
                        </div>
                        <div class="modal-footer">
                            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                            <button type="button" class="btn btn-primary" onclick="updateInvoicePreview()">Actualizar Vista Previa</button>
                            <button type="button" class="btn btn-success" onclick="doPrint()">Imprimir</button>
                        </div>
                    </div>
                </div>
            </div>
        `;
        document.body.insertAdjacentHTML('beforeend', modalHTML);
        addStyleToHead();
    }
  
    // Show modal and generate initial preview
    const modal = new bootstrap.Modal(document.getElementById('printInvoiceModal'));
    modal.show();
    updateInvoicePreview();
}

function updateInvoicePreview() {
    const printDiv = document.getElementById('printInvoice');
    const companyName = document.getElementById('companyName').value;
    const companyAddress = document.getElementById('companyAddress').value;
    const additionalInfo = document.getElementById('additionalInfo').value;
    const footerText = document.getElementById('footerText').value;
    const primaryColor = document.getElementById('primaryColor').value;
    const fontFamily = document.getElementById('fontFamily').value;
  
    const items = Array.from(document.querySelectorAll('#invoiceItemsTable tbody tr')).map(row => ({
        code: row.cells[0].textContent,
        description: row.cells[1].textContent,
        quantity: row.cells[2].querySelector('.quantity-input').value,
        price: row.cells[3].querySelector('.price-input').value,
        discount: row.cells[4].querySelector('.discount-input').value,
        subtotal: row.cells[5].textContent
    }));
  
    const customerName = document.getElementById('customerCommercialName').textContent;
    const customerNIT = document.getElementById('customerTaxId').textContent;  // Changed from Tax ID
    const customerAddress = document.getElementById('customerAddress').textContent;
  
    const invoiceHTML = `
        <div style="font-family: ${fontFamily}; color: ${primaryColor};">
            <div class="invoice-header">
                <img src="${document.getElementById('companyLogo').files[0] ? URL.createObjectURL(document.getElementById('companyLogo').files[0]) : ''}" 
                     class="invoice-logo" alt="Logo">
                <h2>${companyName}</h2>
                <p>${companyAddress}</p>
                <p>${additionalInfo}</p>
            </div>
            
            <div class="invoice-details">
                <div class="row">
                    <div class="col-md-6">
                        <strong>Cliente:</strong> ${customerName}<br>
                        <strong>NIT:</strong> ${customerNIT}<br>  <!-- Changed label but kept ID for consistency -->
                        <strong>Dirección:</strong> ${customerAddress}
                    </div>
                    <div class="col-md-6 text-end">
                        <strong>Factura No:</strong> ${document.getElementById('invoiceSeries').value}-${document.getElementById('invoiceNumber').value}<br>
                        <strong>Fecha:</strong> ${document.getElementById('invoiceDate').value}
                    </div>
                </div>
            </div>
            
            <table class="invoice-items-table">
                <thead style="background-color: ${primaryColor}; color: white;">
                    <tr>
                        <th>Código</th>
                        <th>Descripción</th>
                        <th>Cantidad</th>
                        <th>Precio Unit.</th>
                        <th>Descuento</th>
                        <th>Subtotal</th>
                    </tr>
                </thead>
                <tbody>
                    ${items.map(item => `
                        <tr>
                            <td>${item.code}</td>
                            <td>${item.description}</td>
                            <td>${item.quantity}</td>
                            <td>${item.price}</td>
                            <td>${item.discount}%</td>
                            <td>${item.subtotal}</td>
                        </tr>
                    `).join('')}
                </tbody>
            </table>
            
            <div class="invoice-totals">
                <table class="table">
                    <tr>
                        <td><strong>Subtotal:</strong></td>
                        <td>Q${document.getElementById('subtotal').textContent}</td>
                    </tr>
                    <tr>
                        <td><strong>IVA (12%):</strong></td>
                        <td>Q${document.getElementById('iva').textContent}</td>
                    </tr>
                    <tr>
                        <td><strong>Total:</strong></td>
                        <td>Q${document.getElementById('total').textContent}</td>
                    </tr>
                </table>
            </div>
            
            <div class="invoice-footer">
                <p>${footerText}</p>
            </div>
        </div>
    `;
  
    printDiv.innerHTML = invoiceHTML;
}

function doPrint() {
    window.print();
}

// Add Style to Head for Printing
function addStyleToHead() {
    const printStyles = `
        <style>
            @media print {
                body * {
                    visibility: hidden;
                }
                #printInvoice, #printInvoice * {
                    visibility: visible;
                }
                #printInvoice {
                    position: absolute;
                    left: 0;
                    top: 0;
                    width: 100%;
                }
                .no-print {
                    display: none !important;
                }
            }
            
            .invoice-header {
                text-align: center;
                margin-bottom: 20px;
            }
            
            .invoice-logo {
                max-width: 200px;
                margin-bottom: 10px;
            }
            
            .invoice-company-info {
                margin-bottom: 20px;
            }
            
            .invoice-details {
                margin-bottom: 20px;
                padding: 10px;
                border: 1px solid #ddd;
            }
            
            .invoice-items-table {
                width: 100%;
                margin-bottom: 20px;
                border-collapse: collapse;
            }
            
            .invoice-items-table th,
            .invoice-items-table td {
                border: 1px solid #ddd;
                padding: 8px;
            }
            
            .invoice-totals {
                float: right;
                width: 300px;
            }
            
            .invoice-footer {
                clear: both;
                margin-top: 40px;
                text-align: center;
                font-size: 12px;
            }
        </style>
    `;
    document.head.insertAdjacentHTML('beforeend', printStyles);
}

// Initialize Print Modal and Functions
</script>
</body>
</html>
