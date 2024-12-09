<html><head><base href="." />
<title>Panadería la Bendición</title>
<meta charset="UTF-8">
<style>
  :root {
    --primary-color: #8B4513;      /* Dark brown for bread */
    --secondary-color: #DEB887;    /* Light brown for pastries */
    --accent-color: #D2691E;       /* Chocolate color */
    --background-color: #FFF8DC;   /* Cornsilk - warm background */
  }

  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: var(--background-color);
    margin: 0;
    padding: 20px;
  }

  .container {
    max-width: 1200px; /* Increased from 1000px */
    margin: 0 auto;
    background-color: white;
    padding: 20px 30px; /* Increased horizontal padding */
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
  }

  .tabs {
    display: flex;
    flex-wrap: wrap; /* Allow wrapping if needed */
    margin-bottom: 20px;
    border-bottom: 2px solid var(--secondary-color);
    gap: 2px; /* Add small gap between tabs */
  }

  .tab {
    padding: 10px 15px; /* Slightly reduced horizontal padding */
    cursor: pointer;
    background: transparent;
    border: none;
    color: var(--primary-color);
    display: flex;
    align-items: center;
    gap: 5px;
    white-space: nowrap; /* Prevent text wrapping within tabs */
  }

  .tab.active {
    background-color: var(--secondary-color);
    border-radius: 4px 4px 0 0;
  }

  .tab-content {
    display: none;
  }

  .tab-content.active {
    display: block;
  }

  h1 {
    color: var(--primary-color);
    text-align: center;
    margin-bottom: 30px;
    clear: both; /* Add this to ensure title appears below the buttons */
  }

  .ingredient-form, .recipe-form, .production-form {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr auto;
    gap: 10px;
    margin-bottom: 20px;
  }

  .inventory-form {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr auto;
    gap: 10px;
    margin-bottom: 20px;
  }

  input, select {
    padding: 8px;
    border: 1px solid var(--secondary-color);
    border-radius: 4px;
  }

  button {
    background-color: var(--accent-color);
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  button:hover {
    background-color: var(--primary-color);
  }

  table {
    width: 100%;
    border-collapse: collapse;
    margin-bottom: 20px;
  }

  th, td {
    padding: 10px;
    text-align: left;
    border-bottom: 1px solid var(--secondary-color);
  }

  th {
    background-color: var(--secondary-color);
    color: var(--primary-color);
  }

  .cost-summary {
    background-color: var(--secondary-color);
    padding: 15px;
    border-radius: 4px;
    margin-top: 20px;
  }

  .warning {
    color: red;
    font-weight: bold;
  }

  .recipe-container {
    border: 1px solid var(--secondary-color);
    padding: 15px;
    margin-bottom: 15px;
    border-radius: 4px;
  }

  .recipe-ingredients {
    margin: 10px 0;
    padding: 10px;
    background-color: #fff5e6;
    border-radius: 4px;
  }

  .cost-categories {
    margin-top: 20px;
    padding: 15px;
    background-color: #fff5e6;
    border-radius: 4px;
  }

  .cost-category {
    margin: 10px 0;
    display: grid;
    grid-template-columns: 200px 1fr 100px;
    gap: 10px;
    align-items: center;
  }

  .cost-category label {
    font-weight: bold;
  }

  .cost-category input,
  .cost-category select {
    padding: 8px;
    border: 1px solid var(--secondary-color);
    border-radius: 4px;
  }

  .production-form {
    display: grid;
    grid-template-columns: 2fr 1fr auto;
    gap: 10px;
    margin-bottom: 20px;
  }

  .full-width {
    width: 100%;
  }

  .status-pending {
    color: orange;
    font-weight: bold;
  }

  .status-completed {
    color: green;
    font-weight: bold;
  }

  .status-cancelled {
    color: red;
    font-weight: bold;
  }

  .kardex-entry {
    background-color: #f9f9f9;
  }

  .kardex-exit {
    background-color: #fff3f3;
  }

  #kardexTable th, #kardexTable td {
    padding: 8px;
    text-align: right;
  }

  #kardexTable th:first-child,
  #kardexTable td:first-child,
  #kardexTable th:nth-child(2),
  #kardexTable td:nth-child(2),
  #kardexTable th:nth-child(3),
  #kardexTable td:nth-child(3) {
    text-align: left;
  }

  /* Add these styles for the login screen */
  .login-container {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: var(--background-color);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }

  .login-box {
    background: white url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='80' height='80' viewBox='0 0 24 24' fill='%23DEB887' opacity='0.1'%3E%3Cpath d='M12,3.5c4.1,0,7.5,3.4,7.5,7.5c0,4.1-3.4,7.5-7.5,7.5S4.5,15.1,4.5,11C4.5,6.9,7.9,3.5,12,3.5z M12,2C7,2,3,6,3,11c0,5,4,9,9,9s9-4,9-9C21,6,17,2,12,2z M15.7,14.3L12,10.6L8.3,14.3l-1.4-1.4l5.1-5.1l5.1,5.1L15.7,14.3z'/%3E%3C/svg%3E") no-repeat 95% 5%;
    border: 2px solid var(--secondary-color);
    padding: 30px;
    border-radius: 8px;
  }

  .login-box h2 {
    color: var(--primary-color);
    text-align: center;
    margin-bottom: 20px;
  }

  .login-field {
    margin-bottom: 15px;
  }

  .login-field label {
    display: block;
    margin-bottom: 5px;
    color: var(--primary-color);
  }

  .login-field input {
    width: 100%;
    padding: 8px;
    border: 1px solid var(--secondary-color);
    border-radius: 4px;
  }

  .login-error {
    color: red;
    text-align: center;
    margin-bottom: 15px;
    display: none;
  }

  .login-button {
    width: 100%;
    padding: 10px;
    background-color: var(--primary-color);
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
  }

  .login-button:hover {
    background-color: var(--accent-color);
  }

  /* Hide the main container initially */
  .container {
    display: none;
  }

  /* Add to existing CSS */
  .sellers-form {
    padding: 20px;
    background: white;
    border-radius: 8px;
    margin-bottom: 20px;
  }

  .seller-input-form {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr auto;
    gap: 10px;
    margin-bottom: 20px;
  }

  .seller-settlements {
    margin-top: 30px;
    padding: 20px;
    background: #fff5e6;
    border-radius: 8px;
  }

  .settlement-form {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-bottom: 20px;
  }

  .returns-form {
    display: grid;
    grid-template-columns: 1fr 1fr auto;
    gap: 10px;
    margin-top: 20px;
    padding-top: 20px;
    border-top: 1px solid var(--secondary-color);
  }

  /* Add these styles for recipe editing */
  .recipe-edit-form {
    background: #fff5e6;
    padding: 15px;
    border-radius: 4px;
    margin: 10px 0;
  }

  .edit-fields {
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 10px;
    align-items: center;
    margin-bottom: 15px;
  }

  .recipe-ingredients-edit {
    background: white;
    padding: 10px;
    border-radius: 4px;
    margin: 10px 0;
  }

  .ingredient-edit-row {
    display: grid;
    grid-template-columns: 2fr 1fr auto;
    gap: 10px;
    margin: 5px 0;
    align-items: center;
  }

  .edit-buttons {
    display: flex;
    gap: 10px;
    margin-top: 15px;
  }

  .recipe-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
  }

  .edit-button {
    padding: 5px 10px;
    background-color: var(--secondary-color);
    color: var(--primary-color);
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  .edit-button:hover {
    background-color: var(--accent-color);
    color: white;
  }

  /* Add CSS for logout button */
  .logout-button {
    position: absolute;
    top: 20px;
    right: 20px;
    background-color: var(--accent-color);
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
  }

  .logout-button:hover {
    background-color: var(--primary-color);
  }
</style>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.31/jspdf.plugin.autotable.min.js"></script>
</head>
<body>
<div id="loginScreen" class="login-container">
  <div class="login-box">
    <h2>🥨 Panadería la Bendición 🥖</h2>
    <div id="loginError" class="login-error">
      Usuario o contraseña incorrectos
    </div>
    <div class="login-field">
      <label>Usuario:</label>
      <input type="text" id="username" placeholder="Ingrese su usuario">
    </div>
    <div class="login-field">
      <label>Contraseña:</label>
      <input type="password" id="password" placeholder="Ingrese su contraseña">
    </div>
    <button class="login-button" onclick="login()">Ingresar</button>
  </div>
</div>

<div class="container">
  <button onclick="logout()" class="logout-button">Cerrar Sesión</button>
  <div style="margin-bottom: 20px;">
    <button onclick="generateTotalInventoryReport()" style="float: left;">
      Generar Reporte de Inventario Total
    </button>
    <button onclick="generateSalesReport()" style="float: left; margin-left: 10px;">
      Generar Reporte de Ventas
    </button>
    <h1>🥨 Panadería la Bendición 🥖</h1>
    <div style="clear: both;"></div> <!-- Add this div to ensure proper clearfix -->
  </div>

  <div class="tabs">
    <button class="tab" onclick="showTab('settings')">⚙️ Configuración</button>
    <button class="tab active" onclick="showTab('costs')">💰 Costos</button>
    <button class="tab" onclick="showTab('inventory')">📦 Inventario</button>
    <button class="tab" onclick="showTab('recipes')">📝 Recetas</button>
    <button class="tab" onclick="showTab('production')">🏭 Órdenes de Producción</button>
    <button class="tab" onclick="showTab('finished')">🥖 Producto Terminado</button>
    <button class="tab" onclick="showTab('kardex')">📊 Kardex</button>
    <button class="tab" onclick="showTab('exitOrders')">🚚 Órdenes de Salida</button>
    <button class="tab" onclick="showTab('sellers')">👥 Vendedores</button>
  </div>

  <div id="settingsTab" class="tab-content">
    <h3>Configuración de la Panadería</h3>
    
    <div style="display: grid; gap: 20px; padding: 20px; background: white; border-radius: 8px;">
      <div class="settings-section">
        <h4>Información General</h4>
        <div class="settings-form">
          <label>Nombre de la Panadería:</label>
          <input type="text" id="bakeryName" placeholder="Nombre de la panadería">
          
          <label>Dirección:</label>
          <input type="text" id="bakeryAddress" placeholder="Dirección">
          
          <label>Teléfono:</label>
          <input type="text" id="bakeryPhone" placeholder="Teléfono">
          
          <label>Email:</label>
          <input type="email" id="bakeryEmail" placeholder="Email">
          
          <label>NIT:</label>
          <input type="text" id="bakeryTaxId" placeholder="NIT">
        </div>
      </div>

      <div class="settings-section">
        <h4>Parámetros de Producción</h4>
        <div class="settings-form">
          <label>Capacidad Diaria de Producción (unidades):</label>
          <input type="number" id="dailyCapacity" placeholder="Capacidad diaria">
          
          <label>Horario de Producción:</label>
          <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px;">
            <input type="time" id="productionStart" placeholder="Hora inicio">
            <input type="time" id="productionEnd" placeholder="Hora fin">
          </div>
          
          <label>Días de Trabajo:</label>
          <div class="workdays-selector">
            <label><input type="checkbox" value="1"> Lunes</label>
            <label><input type="checkbox" value="2"> Martes</label>
            <label><input type="checkbox" value="3"> Miércoles</label>
            <label><input type="checkbox" value="4"> Jueves</label>
            <label><input type="checkbox" value="5"> Viernes</label>
            <label><input type="checkbox" value="6"> Sábado</label>
            <label><input type="checkbox" value="0"> Domingo</label>
          </div>
        </div>
      </div>

      <div class="settings-section">
        <h4>Parámetros Financieros</h4>
        <div class="settings-form">
          <label>Moneda:</label>
          <select id="currency">
            <option value="GTQ">Quetzales (GTQ)</option>
            <option value="USD">Dólares (USD)</option>
            <option value="EUR">Euros (EUR)</option>
            <option value="PEN">Soles (PEN)</option>
          </select>
          
          <label>IVA (%):</label>
          <input type="number" id="taxRate" placeholder="Porcentaje de IVA">
          
          <label>Margen de Utilidad por Defecto (%):</label>
          <input type="number" id="defaultProfitMargin" placeholder="Margen de utilidad">
        </div>
      </div>

      <div class="settings-section">
        <h4>Alertas de Inventario</h4>
        <div class="settings-form">
          <label>Días de Anticipación para Alertas:</label>
          <input type="number" id="alertDays" placeholder="Días de anticipación">
          
          <label>Porcentaje Mínimo de Stock (%):</label>
          <input type="number" id="minStockPercentage" placeholder="Porcentaje mínimo">
          
          <label>Email para Notificaciones:</label>
          <input type="email" id="alertEmail" placeholder="Email para alertas">
        </div>
      </div>

      <button onclick="saveSettings()" class="save-settings-btn">Guardar Configuración</button>
    </div>
  </div>

  <div id="costsTab" class="tab-content active">
    <div class="ingredient-form">
      <input type="text" id="ingredientName" placeholder="Nombre del ingrediente">
      <input type="number" id="ingredientQuantity" placeholder="Cantidad">
      <input type="number" id="ingredientPrice" placeholder="Precio">
      <button onclick="addIngredient()">Agregar</button>
    </div>

    <table id="ingredientsTable">
      <thead>
        <tr>
          <th>Ingrediente</th>
          <th>Cantidad</th>
          <th>Precio</th>
          <th>Subtotal</th>
          <th>Acción</th>
        </tr>
      </thead>
      <tbody id="ingredientsList">
      </tbody>
    </table>

    <div class="cost-summary">
      <h3>Resumen de Costos</h3>
      <p>Costo total de ingredientes: $<span id="totalIngredientsCost">0.00</span></p>
      <div>
        <label>Costos adicionales:</label>
        <input type="number" id="additionalCosts" onchange="calculateTotal()" value="0">
      </div>
      <div>
        <label>Unidades a producir:</label>
        <input type="number" id="units" onchange="calculateTotal()" value="1">
      </div>
      <h4>Costo unitario: $<span id="unitCost">0.00</span></h4>
      <div>
        <label>Margen de ganancia (%):</label>
        <input type="number" id="profitMargin" onchange="calculateTotal()" value="30">
      </div>
      <h4>Precio de venta sugerido: $<span id="suggestedPrice">0.00</span></h4>

      <div class="cost-categories">
        <h4>Desglose de Costos Adicionales:</h4>
        
        <div class="cost-category">
          <label>Gastos de Fabricación:</label>
          <input type="number" id="manufacturingCosts" onchange="calculateTotal()" value="0" placeholder="Gastos de fabricación">
          <select id="manufacturingPeriod" onchange="calculateTotal()">
            <option value="daily">Diario</option>
            <option value="weekly">Semanal</option>
            <option value="monthly">Mensual</option>
          </select>
        </div>

        <div class="cost-category">
          <label>Gastos de Mano de Obra:</label>
          <input type="number" id="laborCosts" onchange="calculateTotal()" value="0" placeholder="Gastos de mano de obra">
          <select id="laborPeriod" onchange="calculateTotal()">
            <option value="daily">Diario</option>
            <option value="weekly">Semanal</option>
            <option value="monthly">Mensual</option>
          </select>
        </div>

        <div class="cost-category">
          <label>Gastos Fijos:</label>
          <input type="number" id="fixedCosts" onchange="calculateTotal()" value="0" placeholder="Gastos fijos">
          <select id="fixedPeriod" onchange="calculateTotal()">
            <option value="daily">Diario</option>
            <option value="weekly">Semanal</option>
            <option value="monthly">Mensual</option>
          </select>
        </div>
      </div>
    </div>
  </div>

  <div id="inventoryTab" class="tab-content">
    <div class="inventory-form">
      <input type="text" id="materialName" placeholder="Nombre del material">
      <input type="number" id="stock" placeholder="Stock actual">
      <input type="number" id="minStock" placeholder="Stock mínimo">
      <input type="number" id="materialPrice" placeholder="Precio unitario">
      <button onclick="addMaterial()">Agregar Material</button>
    </div>

    <table>
      <thead>
        <tr>
          <th>Material</th>
          <th>Stock Actual</th>
          <th>Stock Mínimo</th>
          <th>Precio Unitario</th>
          <th>Estado</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody id="materialsList">
      </tbody>
    </table>
  </div>

  <div id="recipesTab" class="tab-content">
    <div class="recipe-form">
      <input type="text" id="recipeName" placeholder="Nombre de la receta">
      <input type="number" id="recipeYield" placeholder="Cantidad de unidades">
      <select id="recipeIngredient">
        <option value="">Seleccionar ingrediente</option>
      </select>
      <button onclick="addRecipe()">Crear Receta</button>
    </div>

    <div id="recipesList"></div>
  </div>

  <div id="productionTab" class="tab-content">
    <div class="production-form">
      <select id="productionRecipe" class="full-width">
        <option value="">Seleccionar receta</option>
      </select>
      <input type="number" id="productionQuantity" placeholder="Cantidad a producir">
      <button onclick="createProductionOrder()">Crear Orden de Producción</button>
    </div>

    <table>
      <thead>
        <tr>
          <th>Orden #</th>
          <th>Receta</th>
          <th>Cantidad</th>
          <th>Estado</th>
          <th>Acción</th>
        </tr>
      </thead>
      <tbody id="productionOrdersList">
      </tbody>
    </table>
  </div>

  <div id="finishedTab" class="tab-content">
    <table>
      <thead>
        <tr>
          <th>Producto</th>
          <th>Stock Actual</th>
          <th>Stock Mínimo</th>
          <th>Costo Unitario</th>
          <th>Precio de Venta</th>
          <th>Estado</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody id="finishedProductsList">
      </tbody>
    </table>
  </div>

  <div id="kardexTab" class="tab-content">
    <div style="margin-bottom: 20px;">
      <select id="kardexType" onchange="updateKardexView()">
        <option value="materials">Kardex de Materias Primas</option>
        <option value="finished">Kardex de Productos Terminados</option>
      </select>
      <select id="kardexItem" onchange="generateKardexReport()">
        <option value="">Seleccionar item</option>
      </select>
    </div>

    <table id="kardexTable">
      <thead>
        <tr>
          <th>Fecha</th>
          <th>Tipo</th>
          <th>Descripción</th>
          <th>Entrada</th>
          <th>Salida</th>
          <th>Existencia</th>
          <th>Costo Unitario</th>
          <th>Costo Total</th>
        </tr>
      </thead>
      <tbody id="kardexList">
      </tbody>
    </table>
  </div>

  <div id="exitOrdersTab" class="tab-content">
    <div class="production-form">
      <select id="exitProduct" class="full-width">
        <option value="">Seleccionar producto</option>
      </select>
      <input type="number" id="exitQuantity" placeholder="Cantidad de salida">
      <input type="text" id="exitReason" placeholder="Motivo de salida">
      <select id="exitSeller">
        <option value="">Seleccionar Vendedor</option>
      </select>
      <button onclick="createExitOrder()">Crear Orden de Salida</button>
    </div>

    <table>
      <thead>
        <tr>
          <th>Orden #</th>
          <th>Producto</th>
          <th>Cantidad</th>
          <th>Motivo</th>
          <th>Vendedor</th>
          <th>Fecha</th>
          <th>Estado</th>
          <th>Acción</th>
        </tr>
      </thead>
      <tbody id="exitOrdersList">
      </tbody>
    </table>
  </div>

  <div id="sellersTab" class="tab-content">
    <div class="sellers-form">
      <h3>Gestión de Vendedores</h3>
      <div class="seller-input-form">
        <input type="text" id="sellerName" placeholder="Nombre del vendedor">
        <input type="text" id="sellerCode" placeholder="Código del vendedor">
        <input type="text" id="sellerPhone" placeholder="Teléfono">
        <input type="text" id="sellerEmail" placeholder="Email">
        <button onclick="addSeller()">Agregar Vendedor</button>
      </div>

      <table>
        <thead>
          <tr>
            <th>Código</th>
            <th>Nombre</th>
            <th>Teléfono</th>
            <th>Email</th>
            <th>Estado</th>
            <th>Acciones</th>
          </tr>
        </thead>
        <tbody id="sellersList">
        </tbody>
      </table>

      <div class="seller-settlements">
        <h3>Liquidaciones de Vendedores</h3>
        <div class="settlement-form">
          <select id="settlementSeller" onchange="loadSellerSales()">
            <option value="">Seleccionar Vendedor</option>
          </select>
          <input type="date" id="settlementDate" onchange="loadSellerSales()">
        </div>

        <div id="sellerSalesSummary" style="margin: 20px 0;">
          <!-- Sales summary will be populated here -->
        </div>

        <div class="returns-form">
          <h4>Devolución de Productos</h4>
          <select id="returnProduct">
            <option value="">Seleccionar Producto</option>
          </select>
          <input type="number" id="returnQuantity" placeholder="Cantidad a devolver">
          <button onclick="returnProducts()">Registrar Devolución</button>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
let ingredients = [];
let inventory = [];
let recipes = [];
let productionOrders = [];
let finishedProducts = [];
let exitOrders = [];
let exitOrderCounter = 1;
let materialTransactions = [];
let finishedProductTransactions = [];
let orderCounter = 1;
let sellers = [];

function login() {
  const username = document.getElementById('username').value;
  const password = document.getElementById('password').value;
  const loginError = document.getElementById('loginError');

  // Check credentials
  if (username === 'Gabriela' && password === '1977362013') {
    // Hide login screen
    document.getElementById('loginScreen').style.display = 'none';
    // Show main container
    document.querySelector('.container').style.display = 'block';
    // Load settings after successful login
    loadSettings();
    // Load saved data
    loadDataFromLocalStorage();
    // Add data saving listeners
    addDataSavingListeners();
  } else {
    // Show error message
    loginError.style.display = 'block';
    // Clear password field
    document.getElementById('password').value = '';
  }
}

// Prevent accessing the system without login
document.addEventListener('DOMContentLoaded', function() {
  // Hide main container initially
  document.querySelector('.container').style.display = 'none';
  // Clear any previous login
  document.getElementById('username').value = '';
  document.getElementById('password').value = '';
  document.getElementById('loginError').style.display = 'none';
});

// Modify the loadSettings function to only work after login
function loadSettings() {
  // Check if user is logged in (main container is visible)
  if (document.querySelector('.container').style.display !== 'block') {
    return;
  }
  // Rest of the loadSettings function remains the same...
}

function showTab(tabName) {
  document.querySelectorAll('.tab-content').forEach(tab => tab.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(tab => tab.classList.remove('active'));
  
  document.getElementById(tabName + 'Tab').classList.add('active');
  event.target.classList.add('active');

  // Update tab icons
  const tabIcons = {
    'settings': '⚙️',
    'costs': '💰',
    'inventory': '📦',
    'recipes': '📝',
    'production': '🏭',
    'finished': '🥖',
    'kardex': '📊',
    'exitOrders': '🚚',
    'sellers': '👥'
  };
  
  document.querySelectorAll('.tab').forEach(tab => {
    const tabText = tab.textContent;
    Object.entries(tabIcons).forEach(([key, icon]) => {
      if (tabText.includes(key)) {
        tab.innerHTML = `${icon} ${tabText}`;
      }
    });
  });

  if (tabName === 'recipes') {
    updateRecipeIngredientsList();
  } else if (tabName === 'production') {
    updateProductionRecipesList();
  } else if (tabName === 'finished') {
    updateFinishedProductsList();
  } else if (tabName === 'kardex') {
    updateKardexView();
  } else if (tabName === 'exitOrders') {
    updateExitProductsList();
    updateSellersList(); // Add this line
  }
}

function updateExitProductsList() {
  const select = document.getElementById('exitProduct');
  select.innerHTML = '<option value="">Seleccionar producto</option>';
  
  finishedProducts.forEach(product => {
    const option = document.createElement('option');
    option.value = product.name;
    option.textContent = product.name;
    select.appendChild(option);
  });
}

function addIngredient() {
  const name = document.getElementById('ingredientName').value;
  const quantity = parseFloat(document.getElementById('ingredientQuantity').value);
  const price = parseFloat(document.getElementById('ingredientPrice').value);

  if (name && quantity && price) {
    ingredients.push({
      name,
      quantity,
      price,
      subtotal: quantity * price
    });

    updateIngredientsTable();
    calculateTotal();
    clearForm('ingredient');
  } else {
    alert('Por favor complete todos los campos');
  }
}

function addMaterial() {
  const name = document.getElementById('materialName').value;
  const stock = parseFloat(document.getElementById('stock').value);
  const minStock = parseFloat(document.getElementById('minStock').value);
  const price = parseFloat(document.getElementById('materialPrice').value);

  if (name && stock && minStock && price) {
    inventory.push({
      name,
      stock,
      minStock,
      price
    });

    updateMaterialsTable();
    clearForm('material');
  } else {
    alert('Por favor complete todos los campos');
  }
}

function updateMaterialsTable() {
  const tbody = document.getElementById('materialsList');
  tbody.innerHTML = '';
  
  inventory.forEach((material, index) => {
    const status = material.stock <= material.minStock ? 
      '<span class="warning">Stock bajo</span>' : 
      'OK';
    
    const row = document.createElement('tr');
    row.innerHTML = `
      <td>${material.name}</td>
      <td>${material.stock}</td>  
      <td>${material.minStock}</td>
      <td>$${material.price.toFixed(2)}</td>
      <td>${status}</td>
      <td>
        <button onclick="adjustInventory('material', ${index})">Ajustar</button>
        <button onclick="deleteMaterial(${index})">Eliminar</button>
      </td>
    `;
    tbody.appendChild(row);
  });
}

function deleteMaterial(index) {
  if (confirm('¿Está seguro que desea eliminar este material?')) {
    inventory.splice(index, 1);
    updateMaterialsTable();
    saveDataToLocalStorage(); // Save changes to localStorage
  }
}

function adjustInventory(type, index) {
  const item = type === 'material' ? inventory[index] : finishedProducts[index];
  const adjustment = parseFloat(prompt(`Ingrese el ajuste de inventario para ${item.name}:\n(Use números positivos para aumentar, negativos para disminuir)`));
  
  if (isNaN(adjustment)) {
    alert('Por favor ingrese un número válido');
    return;
  }

  const reason = prompt('Ingrese el motivo del ajuste:');
  if (!reason) {
    alert('Debe ingresar un motivo para el ajuste');
    return;
  }

  const newStock = item.stock + adjustment;
  if (newStock < 0) {
    alert('El ajuste no puede resultar en un inventario negativo');
    return;
  }

  // Record the transaction in the appropriate kardex
  const transaction = {
    date: new Date(),
    type: adjustment > 0 ? 'entrada' : 'salida',
    description: `Ajuste de inventario - ${reason}`,
    quantity: Math.abs(adjustment),
    balance: newStock,
    unitCost: type === 'material' ? item.price : item.lastUnitCost,
    itemName: item.name
  };

  if (type === 'material') {
    materialTransactions.push(transaction);
    inventory[index].stock = newStock;
    updateMaterialsTable();
  } else {
    finishedProductTransactions.push(transaction);
    finishedProducts[index].stock = newStock;
    updateFinishedProductsList();
  }

  updateKardexView();
  saveDataToLocalStorage();
  alert('Ajuste de inventario realizado con éxito');
}

function addRecipe() {
  const name = document.getElementById('recipeName').value;
  const yield_ = parseFloat(document.getElementById('recipeYield').value);
  
  if (name && yield_) {
    const recipe = {
      name,
      yield: yield_,
      ingredients: [],
      manufacturingCosts: 0,
      manufacturingPeriod: 'daily',
      laborCosts: 0,
      laborPeriod: 'daily',
      fixedCosts: 0,
      fixedPeriod: 'daily',
      profitMargin: 30 // Add default profit margin
    };
    
    recipes.push(recipe);
    updateRecipesList();
    clearForm('recipe');
  } else {
    alert('Por favor complete el nombre y cantidad de la receta');
  }
}

function addIngredientToRecipe(recipeIndex) {
  const ingredientSelect = document.getElementById('recipeIngredient');
  const quantity = parseFloat(prompt('Ingrese la cantidad necesaria:'));
  
  if (quantity && ingredientSelect.value) {
    const ingredient = inventory.find(i => i.name === ingredientSelect.value);
    if (ingredient) {
      recipes[recipeIndex].ingredients.push({
        name: ingredient.name,
        quantity: quantity,
        price: ingredient.price
      });
      updateRecipesList();
    }
  }
}

function updateRecipeIngredientsList() {
  const select = document.getElementById('recipeIngredient');
  select.innerHTML = '<option value="">Seleccionar ingrediente</option>';
  
  inventory.forEach(material => {
    const option = document.createElement('option');
    option.value = material.name;
    option.textContent = material.name;
    select.appendChild(option);
  });
}

function updateRecipesList() {
  const container = document.getElementById('recipesList');
  container.innerHTML = '';
  
  recipes.forEach((recipe, index) => {
    const recipeDiv = document.createElement('div');
    recipeDiv.className = 'recipe-container';
    recipeDiv.id = `recipe${index}`;
    
    let ingredientsCost = 0;
    let ingredientsList = '';
    
    recipe.ingredients.forEach(ing => {
      const cost = ing.quantity * ing.price;
      ingredientsCost += cost;
      ingredientsList += `
        <div>${ing.name} - ${ing.quantity} unidades - $${cost.toFixed(2)}</div>
      `;
    });

    const dailyManufacturing = convertToDailyCost(recipe.manufacturingCosts || 0, recipe.manufacturingPeriod);
    const dailyLabor = convertToDailyCost(recipe.laborCosts || 0, recipe.laborPeriod);
    const dailyFixed = convertToDailyCost(recipe.fixedCosts || 0, recipe.fixedPeriod);
    
    const totalAdditionalCosts = dailyManufacturing + dailyLabor + dailyFixed;
    const totalCost = ingredientsCost + totalAdditionalCosts;
    const unitCost = totalCost / recipe.yield;
    
    const profitMargin = recipe.profitMargin || 30;
    const suggestedPrice = unitCost * (1 + profitMargin/100);

    recipeDiv.innerHTML = `
      <div class="recipe-header">
        <h3>${recipe.name}</h3>
        <button onclick="editRecipe(${index})" class="edit-button">✏️ Editar</button>
      </div>
      <p>Rendimiento: ${recipe.yield} unidades</p>
      <div class="recipe-ingredients">
        <h4>Ingredientes:</h4>
        ${ingredientsList}
      </div>
      
      <div class="cost-categories">
        <h4>Costos Adicionales:</h4>
        <div class="cost-category">
          <label>Gastos de Fabricación:</label>
          <input type="number" value="${recipe.manufacturingCosts || 0}" 
                 onchange="updateRecipeCosts(${index}, 'manufacturing', this.value)">
          <select onchange="updateRecipePeriod(${index}, 'manufacturing', this.value)">
            <option value="daily" ${recipe.manufacturingPeriod === 'daily' ? 'selected' : ''}>Diario</option>
            <option value="weekly" ${recipe.manufacturingPeriod === 'weekly' ? 'selected' : ''}>Semanal</option>
            <option value="monthly" ${recipe.manufacturingPeriod === 'monthly' ? 'selected' : ''}>Mensual</option>
          </select>
        </div>
        
        <div class="cost-category">
          <label>Gastos de Mano de Obra:</label>
          <input type="number" value="${recipe.laborCosts || 0}"
                 onchange="updateRecipeCosts(${index}, 'labor', this.value)">
          <select onchange="updateRecipePeriod(${index}, 'labor', this.value)">
            <option value="daily" ${recipe.laborPeriod === 'daily' ? 'selected' : ''}>Diario</option>
            <option value="weekly" ${recipe.laborPeriod === 'weekly' ? 'selected' : ''}>Semanal</option>
            <option value="monthly" ${recipe.laborPeriod === 'monthly' ? 'selected' : ''}>Mensual</option>
          </select>
        </div>
        
        <div class="cost-category">
          <label>Gastos Fijos:</label>
          <input type="number" value="${recipe.fixedCosts || 0}"
                 onchange="updateRecipeCosts(${index}, 'fixed', this.value)">
          <select onchange="updateRecipePeriod(${index}, 'fixed', this.value)">
            <option value="daily" ${recipe.fixedPeriod === 'daily' ? 'selected' : ''}>Diario</option>
            <option value="weekly" ${recipe.fixedPeriod === 'weekly' ? 'selected' : ''}>Semanal</option>
            <option value="monthly" ${recipe.fixedPeriod === 'monthly' ? 'selected' : ''}>Mensual</option>
          </select>
        </div>
      </div>
      
      <p>Costo de ingredientes: $${ingredientsCost.toFixed(2)}</p>
      <p>Costos adicionales diarios: $${totalAdditionalCosts.toFixed(2)}</p>
      <p>Costo total: $${totalCost.toFixed(2)}</p>
      <p>Costo por unidad: $${unitCost.toFixed(2)}</p>
      
      <div class="cost-category">
        <label>Margen de utilidad (%):</label>
        <input type="number" value="${recipe.profitMargin || 30}" 
               onchange="updateRecipeMargin(${index}, this.value)">
      </div>
      <p><strong>Precio de venta sugerido (${profitMargin}% margen):</strong> $${suggestedPrice.toFixed(2)}</p>
      
      <button onclick="addIngredientToRecipe(${index})">Agregar Ingrediente</button>
    `;
    
    container.appendChild(recipeDiv);
  });
}

function editRecipe(index) {
  const recipe = recipes[index];
  
  // Create edit form HTML
  const editForm = `
    <div class="recipe-edit-form">
      <h4>Editar Receta</h4>
      <div class="edit-fields">
        <label>Nombre:</label>
        <input type="text" id="editRecipeName${index}" value="${recipe.name}">
        
        <label>Rendimiento (unidades):</label>
        <input type="number" id="editRecipeYield${index}" value="${recipe.yield}">
      </div>

      <div class="recipe-ingredients-edit">
        <h4>Ingredientes</h4>
        ${recipe.ingredients.map((ing, ingIndex) => `
          <div class="ingredient-edit-row">
            <input type="text" value="${ing.name}" readonly>
            <input type="number" id="editIngQuantity${index}_${ingIndex}" 
              value="${ing.quantity}" placeholder="Cantidad">
            <button onclick="removeIngredientFromRecipe(${index}, ${ingIndex})">
              🗑️ Eliminar
            </button>
          </div>
        `).join('')}
      </div>
      
      <div class="edit-buttons">
        <button onclick="saveRecipeEdit(${index})">💾 Guardar Cambios</button>
        <button onclick="cancelRecipeEdit(${index})">❌ Cancelar</button>
      </div>
    </div>
  `;
  
  // Replace recipe display with edit form
  document.querySelector(`#recipe${index}`).innerHTML = editForm;
}

function removeIngredientFromRecipe(recipeIndex, ingredientIndex) {
  recipes[recipeIndex].ingredients.splice(ingredientIndex, 1);
  updateRecipesList();
}

function saveRecipeEdit(index) {
  const recipe = recipes[index];
  const newName = document.getElementById(`editRecipeName${index}`).value;
  const newYield = parseInt(document.getElementById(`editRecipeYield${index}`).value);
  
  if (!newName || !newYield) {
    alert('Por favor complete todos los campos obligatorios');
    return;
  }
  
  recipe.name = newName;
  recipe.yield = newYield;
  
  // Update ingredient quantities
  recipe.ingredients.forEach((ing, ingIndex) => {
    const newQuantity = parseFloat(document.getElementById(`editIngQuantity${index}_${ingIndex}`).value);
    if (newQuantity) {
      ing.quantity = newQuantity;
    }
  });
  
  updateRecipesList();
}

function cancelRecipeEdit(index) {
  updateRecipesList();
}

function calculateTotal() {
  const totalIngredients = ingredients.reduce((sum, ing) => sum + ing.subtotal, 0);
  
  // Get values from inputs
  const manufacturingCosts = parseFloat(document.getElementById('manufacturingCosts').value) || 0;
  const laborCosts = parseFloat(document.getElementById('laborCosts').value) || 0;
  const fixedCosts = parseFloat(document.getElementById('fixedCosts').value) || 0;
  
  // Get period selections
  const manufacturingPeriod = document.getElementById('manufacturingPeriod').value;
  const laborPeriod = document.getElementById('laborPeriod').value;
  const fixedPeriod = document.getElementById('fixedPeriod').value;
  
  // Convert all costs to daily basis
  const dailyManufacturing = convertToDailyCost(manufacturingCosts, manufacturingPeriod);
  const dailyLabor = convertToDailyCost(laborCosts, laborPeriod);
  const dailyFixed = convertToDailyCost(fixedCosts, fixedPeriod);
  
  const units = parseInt(document.getElementById('units').value) || 1;
  const profitMargin = parseFloat(document.getElementById('profitMargin').value) || 0;

  const totalAdditionalCosts = dailyManufacturing + dailyLabor + dailyFixed;
  const totalCost = totalIngredients + totalAdditionalCosts;
  const unitCost = totalCost / units;
  const suggestedPrice = unitCost * (1 + profitMargin/100);

  // Update display
  document.getElementById('totalIngredientsCost').textContent = totalIngredients.toFixed(2);
  document.getElementById('unitCost').textContent = unitCost.toFixed(2);
  document.getElementById('suggestedPrice').textContent = suggestedPrice.toFixed(2);
}

// Add this helper function to convert costs to daily basis
function convertToDailyCost(cost, period) {
  switch(period) {
    case 'daily':
      return cost;
    case 'weekly':
      return cost / 7;
    case 'monthly':
      return cost / 30;
    default:
      return cost;
  }
}

// Add the following functions for production orders
function updateProductionRecipesList() {
  const select = document.getElementById('productionRecipe');
  select.innerHTML = '<option value="">Seleccionar receta</option>';
  
  recipes.forEach((recipe, index) => {
    const option = document.createElement('option');
    option.value = index;
    option.textContent = recipe.name;
    select.appendChild(option);
  });
}

function checkInventoryAvailability(recipe, quantity) {
  const missing = [];
  
  recipe.ingredients.forEach(ingredient => {
    const inventoryItem = inventory.find(item => item.name === ingredient.name);
    if (!inventoryItem) {
      missing.push(`${ingredient.name} no existe en inventario`);
    } else if (inventoryItem.stock < (ingredient.quantity * quantity)) {
      missing.push(`${ingredient.name} - Stock insuficiente (Necesario: ${ingredient.quantity * quantity}, Disponible: ${inventoryItem.stock})`);
    }
  });
  
  return missing;
}

function deductInventory(recipe, quantity) {
  recipe.ingredients.forEach(ingredient => {
    const inventoryItem = inventory.find(item => item.name === ingredient.name);
    if (inventoryItem) {
      inventoryItem.stock -= (ingredient.quantity * quantity);
    }
  });
  updateMaterialsTable();
}

function createProductionOrder() {
  const recipeIndex = document.getElementById('productionRecipe').value;
  const quantity = parseInt(document.getElementById('productionQuantity').value);
  
  if (!recipeIndex || !quantity) {
    alert('Por favor seleccione una receta y especifique la cantidad');
    return;
  }
  
  const recipe = recipes[recipeIndex];
  const inventoryCheck = checkInventoryAvailability(recipe, quantity);
  
  if (inventoryCheck.length > 0) {
    alert('No se puede crear la orden:\n' + inventoryCheck.join('\n'));
    return;
  }
  
  const order = {
    id: orderCounter++,
    recipeIndex: parseInt(recipeIndex),
    recipeName: recipe.name,
    quantity: quantity,
    status: 'pending'
  };
  
  productionOrders.push(order);
  updateProductionOrdersList();
  document.getElementById('productionQuantity').value = '';
}

function completeOrder(orderId) {
  const order = productionOrders.find(o => o.id === orderId);
  if (order && order.status === 'pending') {
    const recipe = recipes[order.recipeIndex];
    
    // Record material exits
    recipe.ingredients.forEach(ingredient => {
      const inventoryItem = inventory.find(item => item.name === ingredient.name);
      if (inventoryItem) {
        const quantity = ingredient.quantity * order.quantity;
        materialTransactions.push({
          date: new Date(),
          type: 'salida',
          description: `Orden de producción #${order.id}`,
          quantity: quantity,
          balance: inventoryItem.stock - quantity,
          unitCost: inventoryItem.price,
          itemName: ingredient.name
        });
      }
    });
    
    deductInventory(recipe, order.quantity);
    order.status = 'completed';
    
    // Calculate total unit cost including all costs
    const totalUnitCost = calculateRecipeUnitCost(recipe.name);
    
    // Record finished product entry with total unit cost
    finishedProductTransactions.push({
      date: new Date(),
      type: 'entrada',
      description: `Orden de producción #${order.id} (incluye costos adicionales)`,
      quantity: order.quantity,
      balance: (finishedProducts.find(p => p.name === recipe.name)?.stock || 0) + order.quantity,
      unitCost: totalUnitCost,
      itemName: recipe.name
    });
    
    updateFinishedInventory(recipe.name, order.quantity, totalUnitCost);
    updateProductionOrdersList();
    updateFinishedProductsList();
  }
}

function cancelOrder(orderId) {
  const order = productionOrders.find(o => o.id === orderId);
  if (order && order.status === 'pending') {
    order.status = 'cancelled';
    updateProductionOrdersList();
  }
}

function updateFinishedInventory(productName, quantity, totalUnitCost) {
  let product = finishedProducts.find(p => p.name === productName);
  const recipe = recipes.find(r => r.name === productName);
  const profitMargin = recipe ? recipe.profitMargin : 30; // Default 30% if no recipe found
  const sellingPrice = totalUnitCost * (1 + profitMargin / 100);
  
  if (product) {
    product.stock += quantity;
    product.lastUnitCost = totalUnitCost;
    product.sellingPrice = sellingPrice; // Add selling price
  } else {
    finishedProducts.push({
      name: productName,
      stock: quantity,
      minStock: 10,
      lastUnitCost: totalUnitCost,
      sellingPrice: sellingPrice // Add selling price
    });
  }
}

function calculateRecipeUnitCost(recipeName) {
  const recipe = recipes.find(r => r.name === recipeName);
  if (!recipe) return 0;
  
  // Calculate ingredients cost
  let ingredientsCost = 0;
  recipe.ingredients.forEach(ing => {
    const inventoryItem = inventory.find(item => item.name === ing.name);
    if (inventoryItem) {
      ingredientsCost += ing.quantity * inventoryItem.price;
    }
  });

  // Calculate daily additional costs
  const dailyManufacturing = convertToDailyCost(recipe.manufacturingCosts || 0, recipe.manufacturingPeriod);
  const dailyLabor = convertToDailyCost(recipe.laborCosts || 0, recipe.laborPeriod);
  const dailyFixed = convertToDailyCost(recipe.fixedCosts || 0, recipe.fixedPeriod);
  
  const totalAdditionalCosts = dailyManufacturing + dailyLabor + dailyFixed;
  const totalCost = ingredientsCost + totalAdditionalCosts;
  
  return totalCost / recipe.yield;
}

function updateFinishedProductsList() {
  const tbody = document.getElementById('finishedProductsList');
  tbody.innerHTML = '';
  
  finishedProducts.forEach((product, index) => {
    const status = product.stock <= product.minStock ? 
      '<span class="warning">Stock bajo</span>' : 
      'OK';

    const row = document.createElement('tr');
    row.innerHTML = `
      <td>${product.name}</td>
      <td>${product.stock}</td>
      <td>${product.minStock}</td>
      <td>$${product.lastUnitCost.toFixed(2)}</td>
      <td>$${product.sellingPrice.toFixed(2)}</td>
      <td>${status}</td>
      <td>
        <button onclick="adjustInventory('finished', ${index})">Ajustar</button>
      </td>
    `;
    tbody.appendChild(row);
  });
}

function updateProductionOrdersList() {
  const tbody = document.getElementById('productionOrdersList');
  tbody.innerHTML = '';
  
  productionOrders.forEach(order => {
    const row = document.createElement('tr');
    row.innerHTML = `
      <td>${order.id}</td>
      <td>${order.recipeName}</td>
      <td>${order.quantity}</td>
      <td><span class="status-${order.status}">${order.status}</span></td>
      <td>
        ${order.status === 'pending' ? `
          <button onclick="completeOrder(${order.id})">Completar</button>
          <button onclick="cancelOrder(${order.id})">Cancelar</button>
        ` : ''}
      </td>
    `;
    tbody.appendChild(row);
  });
}

function updateKardexView() {
  const type = document.getElementById('kardexType').value;
  const select = document.getElementById('kardexItem');
  select.innerHTML = '<option value="">Seleccionar item</option>';
  
  if (type === 'materials') {
    inventory.forEach(material => {
      const option = document.createElement('option');
      option.value = material.name;
      option.textContent = material.name;
      select.appendChild(option);
    });
  } else {
    finishedProducts.forEach(product => {
      const option = document.createElement('option');
      option.value = product.name;
      option.textContent = product.name;
      select.appendChild(option);
    });
  }
}

function generateTotalInventoryReport() {
  // Option buttons for format selection
  const formatChoice = confirm('¿Desea generar el reporte en PDF? \nPresione OK para PDF o Cancel para HTML');
  
  if (formatChoice) {
    generatePDFReport();
  } else {
    generateHTMLReport();
  }
}

function generatePDFReport() {
  const { jsPDF } = window.jspdf;
  const doc = new jsPDF();
  
  // Title
  doc.setFontSize(16);
  doc.text('Reporte de Inventario Total', 14, 20);
  doc.setFontSize(11);
  doc.text(`Fecha: ${new Date().toLocaleDateString()}`, 14, 30);

  // Materias Primas Table
  doc.text('Inventario de Materias Primas', 14, 40);
  
  const materialsTableData = inventory.map(material => [
    material.name,
    material.stock.toString(),
    material.minStock.toString(),
    `$${material.price.toFixed(2)}`,
    `$${(material.stock * material.price).toFixed(2)}`
  ]);

  let materialsTotalValue = inventory.reduce((sum, material) => 
    sum + (material.stock * material.price), 0);

  materialsTableData.push([
    'TOTAL',
    '',
    '',
    '',
    `$${materialsTotalValue.toFixed(2)}`
  ]);

  doc.autoTable({
    startY: 45,
    head: [['Material', 'Stock Actual', 'Stock Mínimo', 'Costo Unitario', 'Valor Total']],
    body: materialsTableData,
    theme: 'striped',
    headStyles: { fillColor: [139, 69, 19] }
  });

  // Productos Terminados Table
  doc.text('Inventario de Productos Terminados', 14, doc.lastAutoTable.finalY + 15);

  const productsTableData = finishedProducts.map(product => [
    product.name,
    product.stock.toString(),
    product.minStock.toString(),
    `$${product.lastUnitCost.toFixed(2)}`,
    `$${product.sellingPrice.toFixed(2)}`,
    `$${(product.stock * product.lastUnitCost).toFixed(2)}`,
    `$${(product.stock * product.sellingPrice).toFixed(2)}`
  ]);

  let finishedTotalValue = finishedProducts.reduce((sum, product) => 
    sum + (product.stock * product.lastUnitCost), 0);
  let finishedTotalSalesValue = finishedProducts.reduce((sum, product) => 
    sum + (product.stock * product.sellingPrice), 0);
  
  // Calculate total profit
  let totalProfit = finishedTotalSalesValue - finishedTotalValue;
  let profitPercentage = ((finishedTotalSalesValue - finishedTotalValue) / finishedTotalValue * 100);

  productsTableData.push([
    'TOTAL',
    '',
    '',
    '',
    '',
    `$${finishedTotalValue.toFixed(2)}`,
    `$${finishedTotalSalesValue.toFixed(2)}`
  ]);

  doc.autoTable({
    startY: doc.lastAutoTable.finalY + 20,
    head: [['Producto', 'Stock', 'Stock Min', 'Costo Unit', 'Precio Venta', 'Valor Total (Costo)', 'Valor Total (Venta)']],
    body: productsTableData,
    theme: 'striped',
    headStyles: { fillColor: [139, 69, 19] },
    styles: { fontSize: 8 }
  });

  // Summary with profit calculation
  doc.text('Resumen de Inventario', 14, doc.lastAutoTable.finalY + 15);
  doc.text(`Valor Total de Materias Primas: $${materialsTotalValue.toFixed(2)}`, 14, doc.lastAutoTable.finalY + 25);
  doc.text(`Valor Total de Productos Terminados (Costo): $${finishedTotalValue.toFixed(2)}`, 14, doc.lastAutoTable.finalY + 35);
  doc.text(`Valor Total de Productos Terminados (Venta): $${finishedTotalSalesValue.toFixed(2)}`, 14, doc.lastAutoTable.finalY + 45);
  doc.text(`Valor Total del Inventario (Costo): $${(materialsTotalValue + finishedTotalValue).toFixed(2)}`, 14, doc.lastAutoTable.finalY + 55);
  
  // Add profit information
  doc.text('Análisis de Utilidad', 14, doc.lastAutoTable.finalY + 70);
  doc.text(`Utilidad Total: $${totalProfit.toFixed(2)}`, 14, doc.lastAutoTable.finalY + 80);
  doc.text(`Porcentaje de Utilidad: ${profitPercentage.toFixed(2)}%`, 14, doc.lastAutoTable.finalY + 90);

  // Save PDF
  doc.save('reporte-inventario.pdf');
}

function generateHTMLReport() {
  const reportWindow = window.open('', '_blank');
  // ... (rest of the original HTML report generation code)
}

function generateKardexReport() {
  const type = document.getElementById('kardexType').value;
  const itemName = document.getElementById('kardexItem').value;
  
  // Option buttons for format selection
  const formatChoice = confirm('¿Desea generar el reporte en PDF? \nPresione OK para PDF o Cancel para HTML');
  
  if (formatChoice) {
    generateKardexPDFReport(type, itemName);
  } else {
    generateKardexHTMLReport(type, itemName);
  }
}

function generateKardexPDFReport(type, itemName) {
  if (!itemName) {
    alert('Por favor seleccione un item');
    return;
  }

  const { jsPDF } = window.jspdf;
  const doc = new jsPDF();
  
  const transactions = type === 'materials' 
    ? materialTransactions.filter(t => t.itemName === itemName)
    : finishedProductTransactions.filter(t => t.itemName === itemName);

  // Title
  doc.setFontSize(16);
  doc.text(`Reporte de Kardex - ${itemName}`, 14, 20);
  doc.setFontSize(11);
  doc.text(`Tipo: ${type === 'materials' ? 'Materias Primas' : 'Productos Terminados'}`, 14, 30);
  doc.text(`Fecha: ${new Date().toLocaleDateString()}`, 14, 40);

  const tableData = transactions.map(t => [
    t.date.toLocaleDateString(),
    t.type.toUpperCase(),
    t.description,
    t.type === 'entrada' ? t.quantity.toString() : '',
    t.type === 'salida' ? t.quantity.toString() : '',
    t.balance.toString(),
    `$${t.unitCost.toFixed(2)}`,
    `$${(t.quantity * t.unitCost).toFixed(2)}`
  ]);

  doc.autoTable({
    startY: 45,
    head: [['Fecha', 'Tipo', 'Descripción', 'Entrada', 'Salida', 'Existencia', 'Costo Unit', 'Costo Total']],
    body: tableData,
    theme: 'striped',
    headStyles: { fillColor: [139, 69, 19] }
  });

  // Save PDF
  doc.save(`kardex-${itemName}.pdf`);
}

// Rename the original Kardex HTML report function
function generateKardexHTMLReport(type, itemName) {
  const tbody = document.getElementById('kardexList');
  tbody.innerHTML = '';
  // ... (rest of the original Kardex HTML report generation code)
}

// Add function to create exit order
function createExitOrder() {
  const productName = document.getElementById('exitProduct').value;
  const quantity = parseInt(document.getElementById('exitQuantity').value);
  const reason = document.getElementById('exitReason').value;
  const seller = document.getElementById('exitSeller').value; // New field

  if (!productName || !quantity || !reason || !seller) { // Added seller validation
    alert('Por favor complete todos los campos');
    return;
  }

  const product = finishedProducts.find(p => p.name === productName);
  if (!product) {
    alert('Producto no encontrado');
    return;
  }

  if (product.stock < quantity) {
    alert('Stock insuficiente');
    return;
  }

  const order = {
    id: exitOrderCounter++,
    product: productName,
    quantity: quantity,
    reason: reason,
    seller: seller, // New field
    date: new Date(),
    status: 'pending'
  };

  exitOrders.push(order);
  updateExitOrdersList();
  
  // Clear form
  document.getElementById('exitProduct').value = '';
  document.getElementById('exitQuantity').value = '';
  document.getElementById('exitReason').value = '';
  document.getElementById('exitSeller').value = ''; // Clear seller field
}

function updateExitOrdersList() {
  const tbody = document.getElementById('exitOrdersList');
  tbody.innerHTML = '';
  
  exitOrders.forEach(order => {
    const row = document.createElement('tr');
    row.innerHTML = `
      <td>${order.id}</td>
      <td>${order.product}</td>
      <td>${order.quantity}</td>
      <td>${order.reason}</td>
      <td>${order.seller}</td> <!-- New column -->
      <td>${order.date.toLocaleDateString()}</td>
      <td><span class="status-${order.status}">${order.status}</span></td>
      <td>
        ${order.status === 'pending' ? `
          <button onclick="completeExitOrder(${order.id})">Completar</button>
          <button onclick="cancelExitOrder(${order.id})">Cancelar</button>
        ` : ''}
      </td>
    `;
    tbody.appendChild(row);
  });
}

// Complete exit order function
function completeExitOrder(orderId) {
  const order = exitOrders.find(o => o.id === orderId);
  if (order && order.status === 'pending') {
    const product = finishedProducts.find(p => p.name === order.product);
    
    if (product && product.stock >= order.quantity) {
      // Update finished product stock
      product.stock -= order.quantity;
      
      // Add transaction to kardex
      finishedProductTransactions.push({
        date: new Date(),
        type: 'salida',
        description: `Orden de salida #${order.id} - ${order.reason} - Vendedor: ${order.seller}`,
        quantity: order.quantity,
        balance: product.stock,
        unitCost: product.lastUnitCost,
        itemName: order.product
      });
      
      // Update order status
      order.status = 'completed';
      
      // Update displays
      updateExitOrdersList();
      updateFinishedProductsList();
      updateKardexView();
      
      // Alert success
      alert(`Orden de salida #${order.id} completada exitosamente`);
    } else {
      alert('Error: Stock insuficiente para completar la orden');
    }
  }
}

function cancelExitOrder(orderId) {
  const order = exitOrders.find(o => o.id === orderId);
  if (order && order.status === 'pending') {
    order.status = 'cancelled';
    updateExitOrdersList();
    alert(`Orden de salida #${order.id} cancelada`);
  }
}

function returnProducts() {
  const productName = document.getElementById('returnProduct').value;
  const quantity = parseInt(document.getElementById('returnQuantity').value);
  const seller = document.getElementById('settlementSeller').value;
  
  if (!productName || !quantity || !seller) {
    alert('Por favor complete todos los campos para la devolución');
    return;
  }
  
  const product = finishedProducts.find(p => p.name === productName);
  if (product) {
    // Update stock
    product.stock += quantity;
    
    // Add transaction to kardex
    finishedProductTransactions.push({
      date: new Date(),
      type: 'entrada',
      description: `Devolución de producto - Vendedor: ${seller}`,
      quantity: quantity,
      balance: product.stock,
      unitCost: product.lastUnitCost,
      itemName: productName
    });
    
    // Update displays
    updateFinishedProductsList();
    updateKardexView();
    
    // Clear form
    document.getElementById('returnProduct').value = '';
    document.getElementById('returnQuantity').value = '';
    
    alert(`Devolución registrada exitosamente: ${quantity} unidades de ${productName}`);
  }
}

// Modify updateSellersList to also update return product dropdown
function updateSellersList() {
  const tbody = document.getElementById('sellersList');
  tbody.innerHTML = '';

  sellers.forEach((seller, index) => {
    const row = document.createElement('tr');
    row.innerHTML = `
      <td>${seller.code}</td>
      <td>${seller.name}</td>
      <td>${seller.phone}</td>
      <td>${seller.email}</td>
      <td><span class="status-${seller.status}">${seller.status}</span></td>
      <td>
        <button onclick="toggleSellerStatus(${index})">
          ${seller.status === 'active' ? 'Desactivar' : 'Activar'}
        </button>
        <button onclick="deleteSeller(${index})">Eliminar</button>
      </td>
    `;
    tbody.appendChild(row);
  });

  // Update sellers in exit orders form
  updateSellerDropdowns();
}

function toggleSellerStatus(index) {
  sellers[index].status = sellers[index].status === 'active' ? 'inactive' : 'active';
  updateSellersList();
}

function deleteSeller(index) {
  if (confirm('¿Está seguro de eliminar este vendedor?')) {
    sellers.splice(index, 1);
    updateSellersList();
  }
}

function updateSellerDropdowns() {
  const activeSellerOptions = sellers
    .filter(seller => seller.status === 'active')
    .map(seller => `<option value="${seller.code}">${seller.name}</option>`)
    .join('');

  // Update exit orders seller dropdown
  const exitSellerField = document.getElementById('exitSeller');
  if (exitSellerField) {
    exitSellerField.innerHTML = '<option value="">Seleccionar Vendedor</option>' + activeSellerOptions;
  }

  // Update settlements seller dropdown
  const settlementSellerField = document.getElementById('settlementSeller');
  if (settlementSellerField) {
    settlementSellerField.innerHTML = '<option value="">Seleccionar Vendedor</option>' + activeSellerOptions;
  }
}

function addSeller() {
  const name = document.getElementById('sellerName').value;
  const code = document.getElementById('sellerCode').value;
  const phone = document.getElementById('sellerPhone').value;
  const email = document.getElementById('sellerEmail').value;

  if (!name || !code) {
    alert('Por favor ingrese al menos nombre y código del vendedor');
    return;
  }

  sellers.push({
    name,
    code,
    phone,
    email,
    status: 'active'
  });

  updateSellersList();
  clearSellerForm();
}

function clearSellerForm() {
  document.getElementById('sellerName').value = '';
  document.getElementById('sellerCode').value = '';
  document.getElementById('sellerPhone').value = '';
  document.getElementById('sellerEmail').value = '';
}

function updateSellersList() {
  const tbody = document.getElementById('sellersList');
  tbody.innerHTML = '';

  sellers.forEach((seller, index) => {
    const row = document.createElement('tr');
    row.innerHTML = `
      <td>${seller.code}</td>
      <td>${seller.name}</td>
      <td>${seller.phone}</td>
      <td>${seller.email}</td>
      <td><span class="status-${seller.status}">${seller.status}</span></td>
      <td>
        <button onclick="toggleSellerStatus(${index})">
          ${seller.status === 'active' ? 'Desactivar' : 'Activar'}
        </button>
        <button onclick="deleteSeller(${index})">Eliminar</button>
      </td>
    `;
    tbody.appendChild(row);
  });

  // Update sellers in exit orders form
  updateSellerDropdowns();
}

function clearForm(type) {
  switch(type) {
    case 'ingredient':
      document.getElementById('ingredientName').value = '';
      document.getElementById('ingredientQuantity').value = '';
      document.getElementById('ingredientPrice').value = '';
      break;
    case 'material':
      document.getElementById('materialName').value = '';
      document.getElementById('stock').value = '';
      document.getElementById('minStock').value = '';
      document.getElementById('materialPrice').value = '';
      break;
    case 'recipe':
      document.getElementById('recipeName').value = '';
      document.getElementById('recipeYield').value = '';
      break;
  }
}

// Save all data to localStorage
function saveDataToLocalStorage() {
  try {
    localStorage.setItem('bakeryIngredients', JSON.stringify(ingredients));
    localStorage.setItem('bakeryInventory', JSON.stringify(inventory));
    localStorage.setItem('bakeryRecipes', JSON.stringify(recipes));
    localStorage.setItem('bakeryProductionOrders', JSON.stringify(productionOrders));
    localStorage.setItem('bakeryFinishedProducts', JSON.stringify(finishedProducts));
    localStorage.setItem('bakeryExitOrders', JSON.stringify(exitOrders));
    localStorage.setItem('bakeryMaterialTransactions', JSON.stringify(materialTransactions));
    localStorage.setItem('bakeryFinishedProductTransactions', JSON.stringify(finishedProductTransactions));
    localStorage.setItem('bakeryOrderCounter', orderCounter);
    localStorage.setItem('bakeryExitOrderCounter', exitOrderCounter);
    localStorage.setItem('bakerySellers', JSON.stringify(sellers));
  } catch(e) {
    console.error('Error saving data:', e);
  }
}

// Load all data from localStorage
function loadDataFromLocalStorage() {
  try {
    // Load ingredients
    const savedIngredients = localStorage.getItem('bakeryIngredients');
    if (savedIngredients) ingredients = JSON.parse(savedIngredients);

    // Load inventory
    const savedInventory = localStorage.getItem('bakeryInventory');
    if (savedInventory) inventory = JSON.parse(savedInventory);

    // Load recipes
    const savedRecipes = localStorage.getItem('bakeryRecipes');
    if (savedRecipes) recipes = JSON.parse(savedRecipes);

    // Load production orders
    const savedProductionOrders = localStorage.getItem('bakeryProductionOrders');
    if (savedProductionOrders) {
      productionOrders = JSON.parse(savedProductionOrders);
      // Convert date strings back to Date objects
      productionOrders.forEach(order => {
        if (order.date) order.date = new Date(order.date);
      });
    }

    // Load finished products
    const savedFinishedProducts = localStorage.getItem('bakeryFinishedProducts');
    if (savedFinishedProducts) finishedProducts = JSON.parse(savedFinishedProducts);

    // Load exit orders
    const savedExitOrders = localStorage.getItem('bakeryExitOrders');
    if (savedExitOrders) {
      exitOrders = JSON.parse(savedExitOrders);
      // Convert date strings back to Date objects
      exitOrders.forEach(order => {
        if (order.date) order.date = new Date(order.date);
      });
    }

    // Load transactions
    const savedMaterialTransactions = localStorage.getItem('bakeryMaterialTransactions');
    if (savedMaterialTransactions) {
materialTransactions = JSON.parse(savedMaterialTransactions);
      // Convert date strings back to Date objects
      materialTransactions.forEach(trans => {
        if (trans.date) trans.date = new Date(trans.date);
      });
    }

    const savedFinishedProductTransactions = localStorage.getItem('bakeryFinishedProductTransactions');
    if (savedFinishedProductTransactions) {
      finishedProductTransactions = JSON.parse(savedFinishedProductTransactions);
      // Convert date strings back to Date objects
      finishedProductTransactions.forEach(trans => {
        if (trans.date) trans.date = new Date(trans.date);
      });
    }

    // Load counters
    const savedOrderCounter = localStorage.getItem('bakeryOrderCounter');
    if (savedOrderCounter) orderCounter = parseInt(savedOrderCounter);

    const savedExitOrderCounter = localStorage.getItem('bakeryExitOrderCounter');
    if (savedExitOrderCounter) exitOrderCounter = parseInt(savedExitOrderCounter);

    // Load sellers
    const savedSellers = localStorage.getItem('bakerySellers');
    if (savedSellers) sellers = JSON.parse(savedSellers);

    // Update all views
    updateIngredientsTable();
    updateMaterialsTable();
    updateRecipesList();
    updateProductionOrdersList();
    updateFinishedProductsList();
    updateExitOrdersList();
    updateSellersList();
    calculateTotal();
  } catch(e) {
    console.error('Error loading data:', e);
  }
}

// Add event listener for data saving after any change
function addDataSavingListeners() {
  // Save after any click on buttons
  document.querySelectorAll('button').forEach(button => {
    button.addEventListener('click', () => {
      setTimeout(saveDataToLocalStorage, 100); // Small delay to ensure data is updated
    });
  });

  // Save after any input change
  document.querySelectorAll('input').forEach(input => {
    input.addEventListener('change', () => {
      setTimeout(saveDataToLocalStorage, 100);
    });
  });

  // Save after any select change
  document.querySelectorAll('select').forEach(select => {
    select.addEventListener('change', () => {
      setTimeout(saveDataToLocalStorage, 100);
    });
  });
}

// Logout function
function logout() {
  // Clear any sensitive data if needed
  
  // Hide main container
  document.querySelector('.container').style.display = 'none';
  
  // Show login screen
  document.getElementById('loginScreen').style.display = 'flex';
  
  // Clear login form
  document.getElementById('username').value = '';
  document.getElementById('password').value = '';
  document.getElementById('loginError').style.display = 'none';
}

// Load seller sales
function loadSellerSales() {
  const sellerId = document.getElementById('settlementSeller').value;
  const date = document.getElementById('settlementDate').value;

  if (!sellerId || !date) {
    return;
  }

  // Filter exit orders for this seller and date
  const selectedDate = new Date(date);
  const relevantOrders = exitOrders.filter(order => 
    order.seller === sellerId && 
    order.date.toLocaleDateString() === selectedDate.toLocaleDateString() &&
    order.status === 'completed'
  );

  // Calculate totals
  let totalItems = 0;
  let totalCost = 0;
  let totalSales = 0;

  const productSummary = {};

  relevantOrders.forEach(order => {
    const product = finishedProducts.find(p => p.name === order.product);
    if (product) {
      totalItems += order.quantity;
      const cost = order.quantity * product.lastUnitCost;
      const sales = order.quantity * product.sellingPrice;
      totalCost += cost;
      totalSales += sales;

      // Accumulate product summary
      if (!productSummary[order.product]) {
        productSummary[order.product] = {
          quantity: 0,
          cost: 0,
          sales: 0
        };
      }
      productSummary[order.product].quantity += order.quantity;
      productSummary[order.product].cost += cost;
      productSummary[order.product].sales += sales;
    }
  });

  // Generate summary HTML
  const seller = sellers.find(s => s.code === sellerId);
  const summaryDiv = document.getElementById('sellerSalesSummary');
  summaryDiv.innerHTML = `
    <h4>Resumen de Ventas</h4>
    <p><strong>Vendedor:</strong> ${seller ? seller.name : ''}</p>
    <p><strong>Fecha:</strong> ${new Date(date).toLocaleDateString()}</p>
    
    <div style="margin: 20px 0;">
      <h5>Detalle por Producto:</h5>
      <table style="width: 100%; margin-bottom: 20px;">
        <thead>
          <tr>
            <th>Producto</th>
            <th>Cantidad</th>
            <th>Costo Total</th>
            <th>Venta Total</th>
            <th>Utilidad</th>
          </tr>
        </thead>
        <tbody>
          ${Object.entries(productSummary).map(([product, data]) => `
            <tr>
              <td>${product}</td>
              <td>${data.quantity}</td>
              <td>$${data.cost.toFixed(2)}</td>
              <td>$${data.sales.toFixed(2)}</td>
              <td>$${(data.sales - data.cost).toFixed(2)}</td>
            </tr>
          `).join('')}
        </tbody>
      </table>
    </div>

    <div style="background-color: #fff5e6; padding: 15px; border-radius: 4px;">
      <h5>Totales del Día:</h5>
      <p><strong>Total de Unidades Vendidas:</strong> ${totalItems}</p>
      <p><strong>Costo Total:</strong> $${totalCost.toFixed(2)}</p>
      <p><strong>Ventas Totales:</strong> $${totalSales.toFixed(2)}</p>
      <p><strong>Utilidad:</strong> $${(totalSales - totalCost).toFixed(2)}</p>
      <p><strong>Margen de Utilidad:</strong> ${((totalSales - totalCost) / totalCost * 100).toFixed(2)}%</p>
    </div>
  `;

  // Update return product dropdown with products from today's orders
  const returnProductSelect = document.getElementById('returnProduct');
  returnProductSelect.innerHTML = '<option value="">Seleccionar Producto</option>';
  
  Object.keys(productSummary).forEach(product => {
    const option = document.createElement('option');
    option.value = product;
    option.textContent = product;
    returnProductSelect.appendChild(option);
  });
}
</script>
</body></html>

