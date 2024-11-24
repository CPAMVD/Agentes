<html><head><base href="."  /><script src="https://code.jquery.com/jquery-3.6.0.min.js"></script><script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script><link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet"><link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet"><script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.17.0/xlsx.full.min.js"></script><style>
body {
  background-color: #8B4513;
  font-family: 'Arial', sans-serif;
  height: 100vh;
  margin: 0;
  padding: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.header {
  position: fixed;
  top: 0;
  left: 0;
  padding: 10px;
  color: white;
  z-index: 1000;
}

.header-title {
  font-family: Arial;
  font-size: 18px;
  margin: 0;
}

.header-subtitle {
  font-family: Arial;
  font-size: 10px;
  margin: 0;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  padding: 20px;
}

.login-container, .menu-container, .agents-container, .admin-container {
  background-color: rgba(255, 255, 255, 0.9);
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
  width: 100%;
  max-width: 800px;
  margin: auto;
}

.church-logo {
  width: 150px;
  height: 150px;
  margin: 0 auto 20px;
}

.btn-primary {
  background-color: #1e42e2;
  border-color: #13338b;
}

.btn-primary:hover {
  background-color: #654321;
  border-color: #654321;
}

.footer {
  text-align: center;
  color: white;
  margin-top: 20px;
}

.menu-btn {
  margin: 10px;
  padding: 10px 20px;
  font-size: 1em;
}

.agents-btn {
  margin: 5px;
  padding: 10px 20px;
  font-size: 1em;
  width: auto;
}

.btn i {
  margin-right: 10px;
}

#menuContainer, #agentsContainer, #attendanceContainer, #adminContainer {
  display: none;
}

.buttons-row {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 10px;
}

.swal2-modal {
  width: 80% !important;
  max-width: 800px !important;
}

.form-preview-image {
  max-width: 200px;
  max-height: 200px;
  margin: 10px 0;
}

.agents-table-container {
  margin-top: 20px;
  overflow-x: auto;
}

.agents-table {
  width: 100%;
  margin-top: 20px;
  background: white;
  border-collapse: collapse;
}

.agents-table th,
.agents-table td {
  padding: 10px;
  border: 1px solid #dee2e6;
  text-align: left;
}

.agents-table th {
  background-color: #8B4513;
  color: white;
}

.agents-table img {
  width: 50px;
  height: 50px;
  object-fit: cover;
  border-radius: 50%;
}

.agents-table tbody tr:hover {
  background-color: #f8f9fa;
}

.signatures {
  display: flex;
  justify-content: space-between;
  margin-top: 100px;
  text-align: center;
}
.signature-line {
  width: 200px;
  border-top: 1px solid black;
  margin-top: 50px;
  margin-bottom: 10px;
}
.signature-title {
  font-weight: bold;
}

#adminContainer {
  display: none;
}
</style></head><body>
<div class="header">
  <h1 class="header-title">Parroquia Santa Teresita</h1>
  <p class="header-subtitle">Bananera, Morales, Izabal - <span id="currentUserDisplay"></span></p>
</div>
<div class="container">
  <div id="loginContainer" class="login-container">
    <div class="text-center">
      <svg class="church-logo" viewBox="0 0 100 100">
        <path d="M50 10 L90 40 L80 40 L80 90 L20 90 L20 40 L10 40 Z" fill="#8B4513"/>
        <rect x="45" y="60" width="10" height="30" fill="#654321"/>
        <circle cx="50" cy="30" r="8" fill="#654321"/>
      </svg>
      <h2 class="mb-4">Parroquia Santa Teresita del Niño Jesús</h2>
      <h4 class="mb-4">Sistema de Gestión de Agentes de Pastoral</h4>
    </div>

    <form id="loginForm">
      <div class="mb-3">
        <label for="username" class="form-label">Usuario</label>
        <input type="text" class="form-control" id="username" required>
      </div>
      <div class="mb-3">
        <label for="password" class="form-label">Contraseña</label>
        <input type="password" class="form-control" id="password" required>
      </div>
      <div class="buttons-row">
        <button type="submit" class="btn btn-primary">Ingresar</button>
        <button type="button" class="btn btn-link" onclick="forgotPassword()">Olvidé mi Contraseña</button>
      </div>
    </form>
  </div>

  <div id="menuContainer" class="menu-container">
    <div class="text-center mb-4">
      <h2>Menú Principal</h2>
    </div>
    <div class="buttons-row">
      <button class="btn btn-primary menu-btn" onclick="showAgentsPanel()" data-permission="zona1">
        <i class="fas fa-church"></i> Zona 1
      </button>
      <button class="btn btn-primary menu-btn" onclick="showAgentsPanel()" data-permission="zona2">
        <i class="fas fa-church"></i> Zona 2
      </button>
      <button class="btn btn-primary menu-btn" onclick="showAgentsPanel()" data-permission="zona3">
        <i class="fas fa-church"></i> Zona 3
      </button>
      <button class="btn btn-primary menu-btn" onclick="showAgentsPanel()" data-permission="zona4">
        <i class="fas fa-church"></i> Zona 4
      </button>
      <button class="btn btn-primary menu-btn" onclick="showAdminPanel()" data-permission="admin">
        <i class="fas fa-cogs"></i> Administración
      </button>
      <button class="btn btn-danger menu-btn" onclick="logout()">
        <i class="fas fa-sign-out-alt"></i> Salir
      </button>
    </div>
  </div>

  <div id="agentsContainer" class="agents-container">
    <div class="text-center mb-4">
      <h2>Agentes de Pastoral</h2>
    </div>
    <div class="buttons-row">
      <button class="btn btn-success agents-btn" onclick="newAgent()">
        <i class="fas fa-cross"></i> Nuevo
      </button>
      <button class="btn btn-warning agents-btn" onclick="showImportDialog()">
        <i class="fas fa-file-import"></i> Importar Excel
      </button>
      <button class="btn btn-primary agents-btn" onclick="editAgent()">
        <i class="fas fa-pray"></i> Editar
      </button>
      <button class="btn btn-danger agents-btn" onclick="deleteAgent()">
        <i class="fas fa-church"></i> Borrar
      </button>
      <button class="btn btn-secondary agents-btn" onclick="backToMenu()">
        <i class="fas fa-door-open"></i> Salir
      </button>
      <button class="btn btn-info agents-btn" onclick="showReports()">
        <i class="fas fa-file-alt"></i> Reportes
      </button>
    </div>
    <div class="agents-table-container">
      <table class="agents-table">
        <thead>
          <tr>
            <th>Foto</th>
            <th>Nombre</th>
            <th>DPI</th>
            <th>No. Celular</th>
            <th>Comunidad</th>
            <th>Oratorio</th>
            <th>Ministerio</th>
            <th>Tiempo de Servicio</th>
          </tr>
        </thead>
        <tbody id="agentsTableBody">
        </tbody>
      </table>
    </div>
  </div>

  <div id="attendanceContainer" class="agents-container">
    <div class="text-center mb-4">
      <h2>Control de Asistencia</h2>
    </div>
    <div class="buttons-row">
      <button class="btn btn-success agents-btn" onclick="newAttendance()">
        <i class="fas fa-calendar-plus"></i> Nueva Asistencia
      </button>
      <button class="btn btn-primary agents-btn" onclick="reportAttendance()">
        <i class="fas fa-calendar-check"></i> Reporte de Asistencia
      </button>
      <button class="btn btn-secondary agents-btn" onclick="backToMenu()">
        <i class="fas fa-door-open"></i> Salir
      </button>
    </div>
  </div>

  <div id="adminContainer" class="agents-container">
    <div class="text-center mb-4">
      <h2>Administración</h2>
    </div>
    <div class="buttons-row">
      <button class="btn btn-primary agents-btn" onclick="showRegisterForm()">
        <i class="fas fa-user-plus"></i> Nuevo Usuario
      </button>
      <button class="btn btn-secondary agents-btn" onclick="adminBackToMenu()">
        <i class="fas fa-door-open"></i> Salir
      </button>
    </div>
  </div>
</div>

<script>
const users = [
  {
    username: 'Maynor',
    password: '1977362013',
    role: 'admin',
    permissions: ['zona1', 'zona2', 'zona3', 'zona4', 'admin'] // Admin has all permissions by default
  }
];

const agentesDB = [];
const ministeriosDB = [
  "Catequista",
  "Delegado", 
  "Ministro E.S.C."
];

const actividadesDB = [
  "Formación Mensual",
  "Retiro Espiritual", 
  "Reunión Extraordinaria"
];

// Function to save data to localStorage
function saveToLocalStorage() {
  localStorage.setItem('agentesDB', JSON.stringify(agentesDB));
  localStorage.setItem('ministeriosDB', JSON.stringify(ministeriosDB));
  localStorage.setItem('actividadesDB', JSON.stringify(actividadesDB));
  localStorage.setItem('users', JSON.stringify(users));
}

// Function to load data from localStorage
function loadFromLocalStorage() {
  const savedAgentes = localStorage.getItem('agentesDB');
  const savedMinisterios = localStorage.getItem('ministeriosDB');
  const savedActividades = localStorage.getItem('actividadesDB');
  const savedUsers = localStorage.getItem('users');

  if (savedAgentes) {
    agentesDB.length = 0; // Clear current array
    agentesDB.push(...JSON.parse(savedAgentes));
  }
  
  if (savedMinisterios) {
    ministeriosDB.length = 0; // Clear current array
    ministeriosDB.push(...JSON.parse(savedMinisterios));
  }
  
  if (savedActividades) {
    actividadesDB.length = 0; // Clear current array
    actividadesDB.push(...JSON.parse(savedActividades));
  }
  
  if (savedUsers) {
    users.length = 0; // Clear current array
    users.push(...JSON.parse(savedUsers));
  }
}

// Add call to load data when page loads
document.addEventListener('DOMContentLoaded', function() {
  loadFromLocalStorage();
  updateAgentsTable(); // Update table with loaded data
});

document.getElementById('loginForm').addEventListener('submit', function(e) {
  e.preventDefault();
  const username = document.getElementById('username').value;
  const password = document.getElementById('password').value;

  const user = users.find(u => u.username === username && u.password === password);

  if (user) {
    // Store current user info in sessionStorage
    sessionStorage.setItem('currentUser', JSON.stringify({
      username: user.username,
      role: user.role,
      permissions: user.permissions
    }));

    // Update header with current user
    document.getElementById('currentUserDisplay').textContent = user.username;

    document.getElementById('loginContainer').style.display = 'none';
    document.getElementById('menuContainer').style.display = 'block';
    
    // Hide unauthorized buttons
    if (user.role !== 'admin') {
      const buttons = document.querySelectorAll('.menu-btn');
      buttons.forEach(btn => {
        const permission = btn.getAttribute('data-permission');
        if (permission && !user.permissions.includes(permission)) {
          btn.style.display = 'none';
        }
      });
    }

    Swal.fire({
      icon: 'success',
      title: '¡Bienvenido!',
      text: `Acceso exitoso como ${user.role === 'admin' ? 'administrador' : 'usuario'}`,
      confirmButtonColor: '#8B4513'
    });
  } else {
    Swal.fire({
      icon: 'error',
      title: 'Error',
      text: 'Usuario o contraseña incorrectos',
      confirmButtonColor: '#8B4513'
    });
  }
});

function showAdminPanel() {
  document.getElementById('menuContainer').style.display = 'none';
  document.getElementById('adminContainer').style.display = 'block';
}

function adminBackToMenu() {
  document.getElementById('adminContainer').style.display = 'none';
  document.getElementById('menuContainer').style.display = 'block';
}

function showRegisterForm() {
  const usersTable = `
    <div class="mb-4">
      <h5>Usuarios Existentes</h5>
      <table class="table table-bordered">
        <thead>
          <tr>
            <th>Usuario</th>
            <th>Rol</th>
            <th>Permisos</th>
          </tr>
        </thead>
        <tbody>
          ${users.map(user => `
            <tr>
              <td>${user.username}</td>
              <td>${user.role === 'admin' ? 'Administrador' : 'Usuario'}</td>
              <td>${user.permissions ? user.permissions.join(', ') : 'Ninguno'}</td>
            </tr>
          `).join('')}
        </tbody>
      </table>
    </div>
  `;

  Swal.fire({
    title: 'Registro de Nuevo Usuario',
    html: `
      ${usersTable}
      <div class="mb-3">
        <input type="text" id="newUsername" class="swal2-input" placeholder="Usuario">
      </div>
      <div class="mb-3">
        <input type="password" id="newPassword" class="swal2-input" placeholder="Contraseña">
      </div>
      <div class="mb-3">
        <input type="password" id="confirmPassword" class="swal2-input" placeholder="Confirmar Contraseña">
      </div>
      <div class="mb-3">
        <label class="form-label">Rol:</label>
        <select class="form-control" id="userRole">
          <option value="user">Usuario</option>
          <option value="admin">Administrador</option>
        </select>
      </div>
      <div class="mb-3">
        <label class="form-label">Permisos:</label>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="permZona1" value="zona1">
          <label class="form-check-label" for="permZona1">Zona 1</label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="permZona2" value="zona2">
          <label class="form-check-label" for="permZona2">Zona 2</label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="permZona3" value="zona3">
          <label class="form-check-label" for="permZona3">Zona 3</label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="permZona4" value="zona4">
          <label class="form-check-label" for="permZona4">Zona 4</label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="permAdmin" value="admin">
          <label class="form-check-label" for="permAdmin">Administración</label>
        </div>
      </div>
    `,
    confirmButtonColor: '#8B4513',
    confirmButtonText: 'Registrar',
    showCancelButton: true,
    cancelButtonText: 'Cancelar',
    width: '800px',
    preConfirm: () => {
      const newUsername = document.getElementById('newUsername').value;
      const newPassword = document.getElementById('newPassword').value;
      const confirmPassword = document.getElementById('confirmPassword').value;
      const role = document.getElementById('userRole').value;
      
      // Get selected permissions
      const permissions = ['zona1', 'zona2', 'zona3', 'zona4', 'admin'].filter(perm => 
        document.getElementById(`perm${perm.charAt(0).toUpperCase() + perm.slice(1)}`).checked
      );

      if (!newUsername || !newPassword) {
        Swal.showValidationMessage('Por favor complete todos los campos');
        return false;
      }

      if (newPassword !== confirmPassword) {
        Swal.showValidationMessage('Las contraseñas no coinciden');
        return false;
      }

      if (users.some(u => u.username === newUsername)) {
        Swal.showValidationMessage('El usuario ya existe');
        return false;
      }

      if (permissions.length === 0) {
        Swal.showValidationMessage('Debe seleccionar al menos un permiso');
        return false;
      }

      users.push({
        username: newUsername,
        password: newPassword,
        role: role,
        permissions: permissions
      });
      saveToLocalStorage();

      return true;
    }
  }).then((result) => {
    if (result.isConfirmed) {
      Swal.fire({
        icon: 'success',
        title: '¡Usuario registrado exitosamente!',
        confirmButtonColor: '#8B4513'
      });
    }
  });
}

function forgotPassword() {
  Swal.fire({
    title: 'Recuperar Contraseña',
    text: 'Por favor, contacte al administrador del sistema',
    icon: 'info',
    confirmButtonColor: '#8B4513'
  });
}

function showAgentsPanel() {
  Swal.fire({
    title: 'Seleccione una opción',
    html: `
      <button class="btn btn-primary m-2" onclick="showAgentsList()">
        <i class="fas fa-users"></i> Agentes de Pastoral
      </button>
      <button class="btn btn-primary m-2" onclick="showAttendanceControl()">
        <i class="fas fa-calendar-alt"></i> Control de Asistencia
      </button>
    `,
    showConfirmButton: false,
    width: '400px'
  });
}

function showAgentsList() {
  Swal.close();
  document.getElementById('menuContainer').style.display = 'none';
  document.getElementById('agentsContainer').style.display = 'block';
  document.getElementById('attendanceContainer').style.display = 'none';
  updateAgentsTable();
}

function showAttendanceControl() {
  Swal.close();
  document.getElementById('menuContainer').style.display = 'none';
  document.getElementById('agentsContainer').style.display = 'none';
  document.getElementById('attendanceContainer').style.display = 'block';
}

function backToMenu() {
  document.getElementById('agentsContainer').style.display = 'none';
  document.getElementById('attendanceContainer').style.display = 'none';
  document.getElementById('menuContainer').style.display = 'block';
}

function newAttendance() {
  Swal.fire({
    title: 'Nueva Asistencia',
    html: `
      <div class="mb-3">
        <label class="form-label">Fecha:</label>
        <input type="date" class="form-control" id="attendanceDate" value="${new Date().toISOString().split('T')[0]}">
      </div>
      <div class="mb-3">
        <label class="form-label">Actividad:</label>
        <div class="d-flex gap-2">
          <select class="form-control" id="activitySelect" onchange="handleActivitySelect()">
            <option value="">Seleccione una actividad</option>
            ${actividadesDB.map(act => `
              <option value="${act}">${act}</option>
            `).join('')}
            <option value="other">Otra actividad...</option>
          </select>
          <button type="button" class="btn btn-secondary" onclick="administrarActividades()">
            <i class="fas fa-cog"></i>
          </button>
        </div>
        <div id="customActivityContainer" style="display: none;" class="mt-2">
          <input type="text" class="form-control" id="customActivity" placeholder="Ingrese el nombre de la actividad">
        </div>
      </div>
      <div class="mb-3">
        <label class="form-label">Filtrar Agentes:</label>
        <div class="d-flex gap-2">
          <input type="text" class="form-control" id="filterAgents" placeholder="Buscar por nombre o DPI" onkeyup="filterAgentsList()">
          <button type="button" class="btn btn-primary" onclick="filterAgentsList()">
            <i class="fas fa-search"></i>
          </button>
        </div>
      </div>
      <div class="mb-3">
        <label class="form-label">Seleccionar Agentes y Estado:</label>
        <div id="agentsListContainer" style="max-height: 400px; overflow-y: auto;">
          ${generateAgentsList(agentesDB)}
        </div>
      </div>
    `,
    confirmButtonText: 'Guardar',
    confirmButtonColor: '#8B4513',
    showCancelButton: true,
    cancelButtonText: 'Cancelar',
    width: '800px',
    preConfirm: () => {
      let attendanceRecords = JSON.parse(localStorage.getItem('attendanceRecords') || '[]');
      agentesDB.forEach((agent, idx) => {
        const status = document.querySelector(`input[name="attendance${idx}"]:checked`).value;
        const justification = document.getElementById(`justificacion${idx}`).files[0] ? 
          'Tiene justificación adjunta' : '';
        const newRecord = {
          date: document.getElementById('attendanceDate').value,
          activity: document.getElementById('activitySelect').value === 'other' ? 
            document.getElementById('customActivity').value : 
            document.getElementById('activitySelect').value,
          agentName: agent.nombre,
          status: status,
          justification: justification
        };
        attendanceRecords.push(newRecord);
      });
      localStorage.setItem('attendanceRecords', JSON.stringify(attendanceRecords));
    }
  });
}

function generateAgentsList(agents) {
  return agents.map((agent, idx) => `
    <div class="card mb-2 agent-card" data-name="${agent.nombre.toLowerCase()}" data-dpi="${agent.dpi}">
      <div class="card-body">
        <h6>${agent.nombre} - ${agent.dpi}</h6>
        <div class="form-check form-check-inline">
          <input class="form-check-input" type="radio" name="attendance${idx}" id="ausente${idx}" value="ausente" checked>
          <label class="form-check-label" for="ausente${idx}">Ausente</label>
        </div>
        <div class="form-check form-check-inline">
          <input class="form-check-input" type="radio" name="attendance${idx}" id="presente${idx}" value="presente">
          <label class="form-check-label" for="presente${idx}">Presente</label>
        </div>
        <div class="form-check form-check-inline">
          <input class="form-check-input" type="radio" name="attendance${idx}" id="justificado${idx}" value="justificado">
          <label class="form-check-label" for="justificado${idx}">Ausente con Justificación</label>
        </div>
        <div id="justificacionContainer${idx}" style="display: none;" class="mt-2">
          <input type="file" class="form-control" id="justificacion${idx}" accept="image/*" 
            onchange="previewJustificacion(${idx})">
          <div id="justificacionPreview${idx}" class="mt-2"></div>
        </div>
      </div>
    </div>
  `).join('');
}

function filterAgentsList() {
  const filterValue = document.getElementById('filterAgents').value.toLowerCase();
  const agentCards = document.querySelectorAll('.agent-card');
  
  agentCards.forEach(card => {
    const name = card.dataset.name;
    const dpi = card.dataset.dpi;
    if (name.includes(filterValue) || dpi.includes(filterValue)) {
      card.style.display = 'block';
    } else {
      card.style.display = 'none';
    }
  });
}

function handleActivitySelect() {
  const select = document.getElementById('activitySelect');
  const customContainer = document.getElementById('customActivityContainer');
  
  if (select.value === 'other') {
    customContainer.style.display = 'block';
  } else {
    customContainer.style.display = 'none';
  }
}

function administrarActividades() {
  let actividadesHTML = actividadesDB.map((actividad, index) => `
    <div class="d-flex align-items-center mb-2">
      <input type="text" class="form-control actividad-input" value="${actividad}" data-index="${index}">
      <button class="btn btn-danger ms-2 btn-sm" onclick="eliminarActividad(${index})">
        <i class="fas fa-trash"></i>
      </button>
    </div>
  `).join('');

  Swal.fire({
    title: 'Administrar Actividades',
    html: `
      <div class="mb-3">
        ${actividadesHTML}
      </div>
      <div class="d-flex gap-2">
        <input type="text" id="nuevaActividad" class="form-control" placeholder="Nueva actividad">
        <button type="button" class="btn btn-success" onclick="agregarActividad()">
          <i class="fas fa-plus"></i>
        </button>
      </div>
    `,
    showCancelButton: true,
    showConfirmButton: true,
    confirmButtonText: 'Guardar Cambios',
    cancelButtonText: 'Cancelar',
    confirmButtonColor: '#8B4513',
    didOpen: () => {
      document.querySelectorAll('.actividad-input').forEach(input => {
        input.addEventListener('change', (e) => {
          const index = e.target.dataset.index;
          actividadesDB[index] = e.target.value;
          saveToLocalStorage(); // Save updated activities
        });
      });
    }
  });
}

function agregarActividad() {
  const nuevaActividad = document.getElementById('nuevaActividad').value.trim();
  if (nuevaActividad) {
    actividadesDB.push(nuevaActividad);
    saveToLocalStorage(); // Save updated activities
    administrarActividades();
  }
}

function eliminarActividad(index) {
  Swal.fire({
    title: '¿Está seguro?',
    text: `¿Realmente desea eliminar la actividad "${actividadesDB[index]}"?`,
    icon: 'warning',
    showCancelButton: true,
    confirmButtonColor: '#dc3545',
    cancelButtonColor: '#8B4513',
    confirmButtonText: 'Sí, eliminar',
    cancelButtonText: 'Cancelar'
  }).then((result) => {
    if (result.isConfirmed) {
      actividadesDB.splice(index, 1);
      saveToLocalStorage(); // Save updated activities
      administrarActividades();
      Swal.fire({
        title: 'Eliminado',
        text: 'La actividad ha sido eliminada exitosamente',
        icon: 'success',
        confirmButtonColor: '#8B4513'
      });
    }
  });
}

function previewJustificacion(idx) {
  const file = document.getElementById(`justificacion${idx}`).files[0];
  if (file) {
    const reader = new FileReader();
    reader.onload = function(e) {
      const preview = document.getElementById(`justificacionPreview${idx}`);
      preview.innerHTML = `
        <img src="${e.target.result}" alt="Justificación" style="max-width: 200px; max-height: 200px;">
      `;
    }
    reader.readAsDataURL(file);
  }
}

function reportAttendance() {
  Swal.fire({
    title: 'Reporte de Asistencia',
    html: `
      <div class="mb-3">
        <label class="form-label">Fecha Inicio:</label>
        <input type="date" class="form-control" id="startDate">
      </div>
      <div class="mb-3">
        <label class="form-label">Fecha Fin:</label>
        <input type="date" class="form-control" id="endDate">
      </div>
      <div class="mb-3">
        <label class="form-label">Agente:</label>
        <select class="form-control" id="agentFilter">
          <option value="">Todos los agentes</option>
          ${agentesDB.map(agent => `
            <option value="${agent.nombre}">${agent.nombre}</option>
          `).join('')}
        </select>
      </div>
      <div class="mb-3">
        <label class="form-label">Actividad:</label>
        <select class="form-control" id="activityFilter">
          <option value="">Todas las actividades</option>
          ${actividadesDB.map(activity => `
            <option value="${activity}">${activity}</option>
          `).join('')}
        </select>
      </div>
      <div class="mb-3">
        <label class="form-label">Estado:</label>
        <select class="form-control" id="statusFilter">
          <option value="">Todos los estados</option>
          <option value="presente">Presente</option>
          <option value="ausente">Ausente</option>
          <option value="justificado">Ausente con Justificación</option>
        </select>
      </div>
      <div class="buttons-row mt-3">
        <button class="btn btn-success" onclick="generateAttendanceReport('excel')">
          <i class="fas fa-file-excel"></i> Exportar a Excel
        </button>
        <button class="btn btn-danger" onclick="generateAttendanceReport('pdf')">
          <i class="fas fa-file-pdf"></i> Exportar a PDF
        </button>
      </div>
    `,
    showCancelButton: true,
    showConfirmButton: false,
    cancelButtonText: 'Cerrar',
    width: '600px'
  });
}

function generateAttendanceReport(type) {
  const startDate = document.getElementById('startDate').value;
  const endDate = document.getElementById('endDate').value;
  const agent = document.getElementById('agentFilter').value;
  const status = document.getElementById('statusFilter').value;

  let attendanceRecords = JSON.parse(localStorage.getItem('attendanceRecords') || '[]');

  let filteredRecords = attendanceRecords.filter(record => {
    const dateMatches = (!startDate || record.date >= startDate) && 
                       (!endDate || record.date <= endDate);
    const agentMatches = !agent || record.agentName === agent;
    const statusMatches = !status || record.status === status;
    const activityMatches = !document.getElementById('activityFilter').value || 
                           record.activity === document.getElementById('activityFilter').value;
    
    return dateMatches && agentMatches && statusMatches && activityMatches;
  });

  // Group records by agent
  const groupedRecords = {};
  const months = [];
  const activities = new Set();
  const totals = {};

  filteredRecords.forEach(record => {
    const month = new Date(record.date).toLocaleString('es-ES', { month: 'long' });
    if (!months.includes(month)) {
      months.push(month);
    }
    
    activities.add(record.activity);
    
    if (!groupedRecords[record.agentName]) {
      groupedRecords[record.agentName] = {};
      totals[record.agentName] = {
        presente: 0,
        ausente: 0,
        justificado: 0
      };
    }
    
    if (!groupedRecords[record.agentName][month]) {
      groupedRecords[record.agentName][month] = {};
    }
    
    groupedRecords[record.agentName][month][record.activity] = record.status;
    totals[record.agentName][record.status]++;
  });

  if (type === 'excel') {
    let csvContent = "data:text/csv;charset=utf-8,";
    
    // Header row with months, activities and dates
    csvContent += "Agente," + months.map(month => 
      Array.from(activities).map(activity => `${month} - ${activity} (Fecha)`).join(',')
    ).join(',') + ",Total Presentes,Total Ausentes,Total Justificados\n";
    
    // Data rows with symbols
    Object.keys(groupedRecords).forEach(agent => {
      let row = [agent];
      months.forEach(month => {
        activities.forEach(activity => {
          const record = filteredRecords.find(r => 
            r.agentName === agent && 
            new Date(r.date).toLocaleString('es-ES', { month: 'long' }) === month &&
            r.activity === activity
          );
          const status = record ? record.status : 'N/A';
          let symbol = 'N/A';
          if (status === 'presente') symbol = '✓';
          else if (status === 'ausente') symbol = 'X';
          else if (status === 'justificado') symbol = '■';
          row.push(`${symbol}<br>${record ? record.date : ''}`);
        });
      });
      row.push(totals[agent].presente || 0);
      row.push(totals[agent].ausente || 0);
      row.push(totals[agent].justificado || 0);
      csvContent += row.join(',') + "\n";
    });

    const encodedUri = encodeURI(csvContent);
    const link = document.createElement("a");
    link.setAttribute("href", encodedUri);
    link.setAttribute("download", `reporte_asistencia_${new Date().toISOString().slice(0,10)}.csv`);
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  } else {
    // For PDF/Print version
    const printContent = `
      <html>
        <head>
          <title>Reporte de Asistencia</title>
          <style>
            table { width: 100%; border-collapse: collapse; margin-bottom: 20px; }
            th, td { border: 1px solid black; padding: 8px; text-align: left; }
            th { background-color: #8B4513; color: white; }
            .totals { background-color: #f5f5f5; font-weight: bold; }
            .presente { color: green; font-size: 16px; }
            .ausente { color: red; font-size: 16px; }
            .justificado { color: #FFD700; font-size: 16px; }
            .signatures {
              display: flex;
              justify-content: space-between;
              margin-top: 100px;
              text-align: center;
            }
            .signature-line {
              width: 200px;
              border-top: 1px solid black;
              margin-top: 50px;
              margin-bottom: 10px;
            }
            .signature-title {
              font-weight: bold;
            }
          </style>
        </head>
        <body>
          <h2>Reporte de Asistencia</h2>
          <h3>Período: ${startDate || 'Inicio'} - ${endDate || 'Fin'}</h3>
          ${agent ? `<h4>Agente: ${agent}</h4>` : ''}
          ${status ? `<h4>Estado: ${status}</h4>` : ''}
          <table>
            <thead>
              <tr>
                <th>Agente</th>
                ${months.map(month => 
                  Array.from(activities).map(activity => 
                    `<th>${month}<br>${activity}<br>Fecha</th>`
                  ).join('')
                ).join('')}
                <th>Total Presentes</th>
                <th>Total Ausentes</th>
                <th>Total Justificados</th>
              </tr>
            </thead>
            <tbody>
              ${Object.keys(groupedRecords).map(agent => `
                <tr>
                  <td>${agent}</td>
                  ${months.map(month => 
                    Array.from(activities).map(activity => {
                      const record = filteredRecords.find(r => 
                        r.agentName === agent && 
                        new Date(r.date).toLocaleString('es-ES', { month: 'long' }) === month &&
                        r.activity === activity
                      );
                      const status = record ? record.status : 'N/A';
                      let symbol = 'N/A';
                      if (status === 'presente') symbol = '<span class="presente">✓</span>';
                      else if (status === 'ausente') symbol = '<span class="ausente">✗</span>';
                      else if (status === 'justificado') symbol = '<span class="justificado">■</span>';
                      return `<td>${symbol}<br><span style="font-size: 0.7em;">${record ? record.date : ''}</span></td>`;
                    }).join('')
                  ).join('')}
                  <td class="totals">${totals[agent].presente || 0}</td>
                  <td class="totals">${totals[agent].ausente || 0}</td>
                  <td class="totals">${totals[agent].justificado || 0}</td>
                </tr>
              `).join('')}
            </tbody>
          </table>

          <div class="signatures">
            <div>
              <div class="signature-line"></div>
              <div class="signature-title">Asesor(a)</div>
            </div>
            <div>
              <div class="signature-line"></div>
              <div class="signature-title">Formador</div>
            </div>
            <div>
              <div class="signature-line"></div>
              <div class="signature-title">Formador 2</div>
            </div>
          </div>
        </body>
      </html>
    `;
    
    const printWindow = window.open('', '', 'height=600,width=800');
    printWindow.document.write(printContent);
    printWindow.document.close();
    printWindow.print();
  }
}

function logout() {
  document.getElementById('menuContainer').style.display = 'none';
  document.getElementById('loginContainer').style.display = 'block';
  document.getElementById('loginForm').reset();
  
  // Clear user display
  document.getElementById('currentUserDisplay').textContent = '';
}

function newAgent() {
  let photoPreview = '';
  
  Swal.fire({
    title: 'Nuevo Agente de Pastoral',
    html: `
      <form id="newAgentForm" class="text-start">
        <div class="mb-3">
          <label class="form-label">Foto:</label>
          <input type="file" class="form-control" id="photo" accept="image/*" onchange="previewPhoto(event)">
          <div id="photoPreview"></div>
        </div>
        <div class="mb-3">
          <label class="form-label">Nombre:</label>
          <input type="text" class="form-control" id="nombre" required>
        </div>
        <div class="mb-3">
          <label class="form-label">DPI:</label>
          <input type="text" class="form-control" id="dpi" required>
        </div>
        <div class="mb-3">
          <label class="form-label">No. Celular:</label>
          <input type="tel" class="form-control" id="celular" required>
        </div>
        <div class="mb-3">
          <label class="form-label">Comunidad:</label>
          <input type="text" class="form-control" id="comunidad" required>
        </div>
        <div class="mb-3">
          <label class="form-label">Oratorio:</label>
          <input type="text" class="form-control" id="oratorio" required>
        </div>
        <div class="mb-3">
          <label class="form-label">Fecha de Nacimiento:</label>
          <input type="date" class="form-control" id="fechaNacimiento" required>
        </div>
        <div class="mb-3">
          <label class="form-label">Fecha de Inicio:</label>
          <input type="date" class="form-control" id="fechaInicio" required>
        </div>
        <div class="mb-3">
          <label class="form-label">Documentos (PDF):</label>
          <input type="file" class="form-control" id="documentos" accept=".pdf" multiple>
        </div>
        <div class="mb-3">
          <label class="form-label">Ministerio:</label>
          <div class="d-flex gap-2">
            <select class="form-control" id="ministerio" required>
              <option value="">Seleccione un ministerio</option>
              ${ministeriosDB.map(ministerio => `
                <option value="${ministerio}">${ministerio}</option>
              `).join('')}
            </select>
            <button type="button" class="btn btn-secondary" onclick="administrarMinisterios()">
              <i class="fas fa-cog"></i>
            </button>
          </div>
        </div>
      </form>
    `,
    confirmButtonText: 'Guardar',
    confirmButtonColor: '#8B4513',
    showCancelButton: true,
    cancelButtonText: 'Cancelar',
    width: '800px',
    preConfirm: () => {
      const formData = {
        photo: document.getElementById('photo').files[0],
        nombre: document.getElementById('nombre').value,
        dpi: document.getElementById('dpi').value,
        celular: document.getElementById('celular').value,
        comunidad: document.getElementById('comunidad').value,
        oratorio: document.getElementById('oratorio').value,
        fechaNacimiento: document.getElementById('fechaNacimiento').value,
        fechaInicio: document.getElementById('fechaInicio').value,
        documentos: document.getElementById('documentos').files,
        ministerio: document.getElementById('ministerio').value,
        tiempoServicio: calculateServiceTime(document.getElementById('fechaInicio').value),
        hasLinkedRecords: false
      };

      if (formData.photo) {
        const reader = new FileReader();
        reader.onload = function(e) {
          formData.photoUrl = e.target.result;
          agentesDB.push(formData);
          saveToLocalStorage(); // Save updated agents
          updateAgentsTable();
        }
        reader.readAsDataURL(formData.photo);
      } else {
        agentesDB.push(formData);
        saveToLocalStorage(); // Save updated agents
        updateAgentsTable();
      }

      return formData;
    }
  }).then((result) => {
    if (result.isConfirmed) {
      Swal.fire({
        icon: 'success',
        title: '¡Agente guardado exitosamente!',
        confirmButtonColor: '#8B4513'
      });
    }
  });
}

function calculateServiceTime(startDate) {
  const start = new Date(startDate);
  const today = new Date();
  const diffTime = Math.abs(today - start);
  const diffYears = Math.floor(diffTime / (1000 * 60 * 60 * 24 * 365));
  const diffMonths = Math.floor((diffTime % (1000 * 60 * 60 * 24 * 365)) / (1000 * 60 * 60 * 24 * 30));
  return `${diffYears} años y ${diffMonths} meses`;
}

function previewPhoto(event) {
  const file = event.target.files[0];
  if (file) {
    const reader = new FileReader();
    reader.onload = function(e) {
      const preview = document.getElementById('photoPreview');
      preview.innerHTML = `<img src="${e.target.result}" class="form-preview-image">`;
    }
    reader.readAsDataURL(file);
  }
}

function updateAgentsTable() {
  const tableBody = document.getElementById('agentsTableBody');
  tableBody.innerHTML = '';
  
  agentesDB.forEach(agent => {
    const row = document.createElement('tr');
    row.innerHTML = `
      <td>
        ${agent.photoUrl ? 
          `<img src="${agent.photoUrl}" alt="Foto de ${agent.nombre}">` : 
          '<i class="fas fa-user" style="font-size: 24px;"></i>'}
      </td>
      <td>${agent.nombre}</td>
      <td>${agent.dpi}</td>
      <td>${agent.celular}</td>
      <td>${agent.comunidad}</td>
      <td>${agent.oratorio}</td>
      <td>${agent.ministerio}</td>
      <td>${agent.tiempoServicio}</td>
    `;
    tableBody.appendChild(row);
  });
}

function editAgent() {
  if (!agentesDB.length) {
    Swal.fire({
      title: 'No hay agentes',
      text: 'No hay agentes registrados para editar',
      icon: 'info',
      confirmButtonColor: '#8B4513'
    });
    return;
  }

  const agentOptions = agentesDB.map((agent, index) => 
    `<option value="${index}">${agent.nombre} - ${agent.dpi}</option>`
  ).join('');

  Swal.fire({
    title: 'Editar Agente de Pastoral',
    html: `
      <select class="form-control mb-3" id="agentToEdit">
        <option value="">Seleccione un agente para editar</option>
        ${agentOptions}
      </select>
    `,
    showCancelButton: true,
    confirmButtonColor: '#8B4513',
    confirmButtonText: 'Continuar',
    cancelButtonText: 'Cancelar',
    preConfirm: () => {
      const selectedIndex = document.getElementById('agentToEdit').value;
      if (!selectedIndex) {
        Swal.showValidationMessage('Por favor seleccione un agente');
        return false;
      }
      return selectedIndex;
    }
  }).then((result) => {
    if (result.isConfirmed) {
      const selectedIndex = parseInt(result.value);
      const agent = agentesDB[selectedIndex];
      showEditForm(agent, selectedIndex);
    }
  });
}

function showEditForm(agent, index) {
  Swal.fire({
    title: 'Editar Agente de Pastoral',
    html: `
      <form id="editAgentForm" class="text-start">
        <div class="mb-3">
          <label class="form-label">Foto Actual:</label>
          ${agent.photoUrl ? 
            `<img src="${agent.photoUrl}" class="form-preview-image d-block">` : 
            '<p>No hay foto</p>'}
          <label class="form-label">Nueva Foto:</label>
          <input type="file" class="form-control" id="editPhoto" accept="image/*" onchange="previewPhoto(event)">
          <div id="photoPreview"></div>
        </div>
        <div class="mb-3">
          <label class="form-label">Nombre:</label>
          <input type="text" class="form-control" id="editNombre" value="${agent.nombre}" required>
        </div>
        <div class="mb-3">
          <label class="form-label">DPI:</label>
          <input type="text" class="form-control" id="editDpi" value="${agent.dpi}" required>
        </div>
        <div class="mb-3">
          <label class="form-label">No. Celular:</label>
          <input type="tel" class="form-control" id="editCelular" value="${agent.celular}" required>
        </div>
        <div class="mb-3">
          <label class="form-label">Comunidad:</label>
          <input type="text" class="form-control" id="editComunidad" value="${agent.comunidad}" required>
        </div>
        <div class="mb-3">
          <label class="form-label">Oratorio:</label>
          <input type="text" class="form-control" id="editOratorio" value="${agent.oratorio}" required>
        </div>
        <div class="mb-3">
          <label class="form-label">Fecha de Nacimiento:</label>
          <input type="date" class="form-control" id="editFechaNacimiento" value="${agent.fechaNacimiento}" required>
        </div>
        <div class="mb-3">
          <label class="form-label">Fecha de Inicio:</label>
          <input type="date" class="form-control" id="editFechaInicio" value="${agent.fechaInicio}" required>
        </div>
        <div class="mb-3">
          <label class="form-label">Documentos (PDF):</label>
          <input type="file" class="form-control" id="editDocumentos" accept=".pdf" multiple>
          ${agent.documentos ? '<p class="text-info">Ya hay documentos cargados</p>' : ''}
        </div>
        <div class="mb-3">
          <label class="form-label">Ministerio:</label>
          <div class="d-flex gap-2">
            <select class="form-control" id="editMinisterio" required>
              ${ministeriosDB.map(ministerio => `
                <option value="${ministerio}" ${agent.ministerio === ministerio ? 'selected' : ''}>
                  ${ministerio}
                </option>
              `).join('')}
            </select>
            <button type="button" class="btn btn-secondary" onclick="administrarMinisterios()">
              <i class="fas fa-cog"></i>
            </button>
          </div>
        </div>
      </form>
    `,
    confirmButtonText: 'Guardar Cambios',
    confirmButtonColor: '#8B4513',
    showCancelButton: true,
    cancelButtonText: 'Cancelar',
    width: '800px',
    preConfirm: () => {
      const editedAgent = {
        nombre: document.getElementById('editNombre').value,
        dpi: document.getElementById('editDpi').value,
        celular: document.getElementById('editCelular').value,
        comunidad: document.getElementById('editComunidad').value,
        oratorio: document.getElementById('editOratorio').value,
        fechaNacimiento: document.getElementById('editFechaNacimiento').value,
        fechaInicio: document.getElementById('editFechaInicio').value,
        ministerio: document.getElementById('editMinisterio').value,
        tiempoServicio: calculateServiceTime(document.getElementById('editFechaInicio').value),
        hasLinkedRecords: agent.hasLinkedRecords,
        photoUrl: agent.photoUrl // Maintain existing photo if no new one is uploaded
      };

      const photoInput = document.getElementById('editPhoto');
      if (photoInput.files.length > 0) {
        return new Promise((resolve) => {
          const reader = new FileReader();
          reader.onload = function(e) {
            editedAgent.photoUrl = e.target.result;
            resolve(editedAgent);
          }
          reader.readAsDataURL(photoInput.files[0]);
        });
      }

      return editedAgent;
    }
  }).then((result) => {
    if (result.isConfirmed) {
      agentesDB[index] = result.value;
      saveToLocalStorage(); // Save updated agents
      updateAgentsTable();
      
      Swal.fire({
        icon: 'success',
        title: 'Cambios Guardados',
        text: 'Los datos del agente han sido actualizados exitosamente',
        confirmButtonColor: '#8B4513'
      });
    }
  });
}

function deleteAgent() {
  if (!agentesDB.length) {
    Swal.fire({
      title: 'No hay agentes',
      text: 'No hay agentes registrados para eliminar',
      icon: 'info',
      confirmButtonColor: '#8B4513'
    });
    return;
  }

  const deletableAgents = agentesDB.filter(agent => !agent.hasLinkedRecords);

  if (!deletableAgents.length) {
    Swal.fire({
      title: 'No hay agentes disponibles',
      text: 'No hay agentes que se puedan eliminar. Todos tienen registros vinculados.',
      icon: 'warning',
      confirmButtonColor: '#8B4513'
    });
    return;
  }

  const agentOptions = agentesDB.map((agent, index) => {
    if (agent.hasLinkedRecords) {
      return `<option value="${index}" disabled>${agent.nombre} - ${agent.dpi} (Tiene registros vinculados)</option>`;
    }
    return `<option value="${index}">${agent.nombre} - ${agent.dpi}</option>`;
  }).join('');

  Swal.fire({
    title: 'Eliminar Agente de Pastoral',
    html: `
      <p class="text-danger">¡Atención! Esta acción no se puede deshacer.</p>
      <p class="text-info">Nota: Los agentes con registros vinculados no pueden ser eliminados.</p>
      <select class="form-control" id="agentToDelete">
        <option value="">Seleccione un agente para eliminar</option>
        ${agentOptions}
      </select>
    `,
    icon: 'warning',
    showCancelButton: true,
    confirmButtonColor: '#dc3545',
    cancelButtonColor: '#8B4513',
    confirmButtonText: 'Sí, eliminar',
    cancelButtonText: 'Cancelar',
    preConfirm: () => {
      const selectedIndex = document.getElementById('agentToDelete').value;
      if (!selectedIndex) {
        Swal.showValidationMessage('Por favor seleccione un agente');
        return false;
      }
      
      const selectedAgent = agentesDB[selectedIndex];
      if (selectedAgent.hasLinkedRecords) {
        Swal.showValidationMessage('Este agente no puede ser eliminado porque tiene registros vinculados');
        return false;
      }
      
      return selectedIndex;
    }
  }).then((result) => {
    if (result.isConfirmed) {
      const indexToDelete = parseInt(result.value);
      const deletedAgent = agentesDB[indexToDelete].nombre;
      
      Swal.fire({
        title: '¿Está seguro?',
        text: `¿Realmente desea eliminar al agente ${deletedAgent}?`,
        icon: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#dc3545',
        cancelButtonColor: '#8B4513',
        confirmButtonText: 'Sí, eliminar',
        cancelButtonText: 'Cancelar'
      }).then((finalResult) => {
        if (finalResult.isConfirmed) {
          agentesDB.splice(indexToDelete, 1);
          saveToLocalStorage(); // Save updated agents
          updateAgentsTable();
          Swal.fire({
            title: 'Eliminado',
            text: `El agente ${deletedAgent} ha sido eliminado exitosamente`,
            icon: 'success',
            confirmButtonColor: '#8B4513'
          });
        }
      });
    }
  });
}

function administrarMinisterios() {
  let ministeriosHTML = ministeriosDB.map((ministerio, index) => `
    <div class="d-flex align-items-center mb-2">
      <input type="text" class="form-control ministerio-input" value="${ministerio}" data-index="${index}">
      <button class="btn btn-danger ms-2 btn-sm" onclick="eliminarMinisterio(${index})">
        <i class="fas fa-trash"></i>
      </button>
    </div>
  `).join('');

  Swal.fire({
    title: 'Administrar Ministerios',
    html: `
      <div class="mb-3">
        ${ministeriosHTML}
      </div>
      <div class="d-flex gap-2">
        <input type="text" id="nuevoMinisterio" class="form-control" placeholder="Nuevo ministerio">
        <button type="button" class="btn btn-success" onclick="agregarMinisterio()">
          <i class="fas fa-plus"></i>
        </button>
      </div>
    `,
    showCancelButton: true,
    showConfirmButton: true,
    confirmButtonText: 'Guardar Cambios',
    cancelButtonText: 'Cancelar',
    confirmButtonColor: '#8B4513',
    width: '600px',
    didOpen: () => {
      document.querySelectorAll('.ministerio-input').forEach(input => {
        input.addEventListener('change', (e) => {
          const index = e.target.dataset.index;
          ministeriosDB[index] = e.target.value;
          saveToLocalStorage(); // Save updated ministerios
        });
      });
    },
  });
}

function agregarMinisterio() {
  const nuevoMinisterio = document.getElementById('nuevoMinisterio').value.trim();
  if (nuevoMinisterio) {
    ministeriosDB.push(nuevoMinisterio);
    saveToLocalStorage(); // Save updated ministerios
    administrarMinisterios();
  }
}

function eliminarMinisterio(index) {
  const ministerioToDelete = ministeriosDB[index];
  const ministerioInUse = agentesDB.some(agent => agent.ministerio === ministerioToDelete);
  
  if (ministerioInUse) {
    Swal.fire({
      title: 'No se puede eliminar',
      text: 'Este ministerio está siendo usado por uno o más agentes y no puede ser eliminado.',
      icon: 'error',
      confirmButtonColor: '#8B4513'
    });
    return;
  }

  Swal.fire({
    title: '¿Está seguro?',
    text: `¿Realmente desea eliminar el ministerio "${ministeriosDB[index]}"?`,
    icon: 'warning',
    showCancelButton: true,
    confirmButtonColor: '#dc3545',
    cancelButtonColor: '#8B4513',
    confirmButtonText: 'Sí, eliminar',
    cancelButtonText: 'Cancelar'
  }).then((result) => {
    if (result.isConfirmed) {
      ministeriosDB.splice(index, 1);
      saveToLocalStorage(); // Save updated ministerios
      administrarMinisterios();
      Swal.fire({
        title: 'Eliminado',
        text: 'El ministerio ha sido eliminado exitosamente',
        icon: 'success',
        confirmButtonColor: '#8B4513'
      });
    }
  });
}

function updateMinisterioSelect() {
  const ministerioSelects = document.querySelectorAll('select#ministerio');
  ministerioSelects.forEach(select => {
    const currentValue = select.value;
    select.innerHTML = `
      <option value="">Seleccione un ministerio</option>
      ${ministeriosDB.map(ministerio => `
        <option value="${ministerio}" ${currentValue === ministerio ? 'selected' : ''}>
          ${ministerio}
        </option>
      `).join('')}
    `;
  });
}

function showReports() {
  Swal.fire({
    title: 'Generar Reportes',
    html: `
      <div class="text-start">
        <h5>Reportes Generales</h5>
        <div class="mb-3">
          <button class="btn btn-success w-100 mb-2" onclick="generateGeneralReport('excel')">
            <i class="fas fa-file-excel"></i> Reporte General en Excel
          </button>
          <button class="btn btn-danger w-100" onclick="generateGeneralReport('pdf')">
            <i class="fas fa-file-pdf"></i> Reporte General en PDF
          </button>
        </div>
        <h5>Reportes por Ministerio</h5>
        <div class="mb-3">
          <select class="form-control mb-2" id="ministerioReporte">
            <option value="">Seleccione un ministerio</option>
            ${ministeriosDB.map(ministerio => `
              <option value="${ministerio}">${ministerio}</option>
            `).join('')}
          </select>
          <button class="btn btn-success w-100 mb-2" onclick="generateMinisterioReport('excel')">
            <i class="fas fa-file-excel"></i> Reporte por Ministerio en Excel
          </button>
          <button class="btn btn-danger w-100" onclick="generateMinisterioReport('pdf')">
            <i class="fas fa-file-pdf"></i> Reporte por Ministerio en PDF
          </button>
        </div>
      </div>
    `,
    showCancelButton: true,
    showConfirmButton: false,
    cancelButtonText: 'Cerrar',
    width: '600px'
  });
}

function generateGeneralReport(type) {
  const date = new Date().toISOString().slice(0,10);
  
  if (type === 'excel') {
    let csvContent = "data:text/csv;charset=utf-8,";
    
    csvContent += "Nombre,DPI,No. Celular,Comunidad,Oratorio,Ministerio,Tiempo de Servicio\n";
    
    agentesDB.forEach(agent => {
      csvContent += `${agent.nombre},${agent.dpi},${agent.celular},${agent.comunidad},${agent.oratorio},${agent.ministerio},${agent.tiempoServicio}\n`;
    });
    
    const encodedUri = encodeURI(csvContent);
    const link = document.createElement("a");
    link.setAttribute("href", encodedUri);
    link.setAttribute("download", `reporte_general_agentes_${date}.csv`);
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
    
    Swal.fire({
      icon: 'success',
      title: 'Reporte Generado',
      text: 'El reporte en Excel ha sido generado exitosamente',
      confirmButtonColor: '#8B4513'
    });
  } else {
    const printContent = `
      <html>
        <head>
          <title>Reporte General de Agentes de Pastoral</title>
          <style>
            table { width: 100%; border-collapse: collapse; }
            th, td { border: 1px solid black; padding: 8px; text-align: left; }
            th { background-color: #8B4513; color: white; }
          </style>
        </head>
        <body>
          <h2>Reporte General de Agentes de Pastoral</h2>
          <h3>Fecha: ${date}</h3>
          <table>
            <thead>
              <tr>
                <th>Nombre</th>
                <th>DPI</th>
                <th>No. Celular</th>
                <th>Comunidad</th>
                <th>Oratorio</th>
                <th>Ministerio</th>
                <th>Tiempo de Servicio</th>
              </tr>
            </thead>
            <tbody>
              ${agentesDB.map(agent => `
                <tr>
                  <td>${agent.nombre}</td>
                  <td>${agent.dpi}</td>
                  <td>${agent.celular}</td>
                  <td>${agent.comunidad}</td>
                  <td>${agent.oratorio}</td>
                  <td>${agent.ministerio}</td>
                  <td>${agent.tiempoServicio}</td>
                </tr>
              `).join('')}
            </tbody>
          </table>
        </body>
      </html>
    `;
    
    const printWindow = window.open('', '', 'height=600,width=800');
    printWindow.document.write(printContent);
    printWindow.document.close();
    printWindow.print();
  }
}

function generateMinisterioReport(type) {
  const ministerio = document.getElementById('ministerioReporte').value;
  if (!ministerio) {
    Swal.fire({
      icon: 'error',
      title: 'Error',
      text: 'Por favor seleccione un ministerio',
      confirmButtonColor: '#8B4513'
    });
    return;
  }
  
  const date = new Date().toISOString().slice(0,10);
  const filteredAgents = agentesDB.filter(agent => agent.ministerio === ministerio);
  
  if (type === 'excel') {
    let csvContent = "data:text/csv;charset=utf-8,";
    
    csvContent += "Nombre,DPI,No. Celular,Comunidad,Oratorio,Tiempo de Servicio\n";
    
    filteredAgents.forEach(agent => {
      csvContent += `${agent.nombre},${agent.dpi},${agent.celular},${agent.comunidad},${agent.oratorio},${agent.tiempoServicio}\n`;
    });
    
    const encodedUri = encodeURI(csvContent);
    const link = document.createElement("a");
    link.setAttribute("href", encodedUri);
    link.setAttribute("download", `reporte_${ministerio}_${date}.csv`);
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
    
    Swal.fire({
      icon: 'success',
      title: 'Reporte Generado',
      text: `El reporte de ${ministerio} en Excel ha sido generado exitosamente`,
      confirmButtonColor: '#8B4513'
    });
  } else {
    const printContent = `
      <html>
        <head>
          <title>Reporte de Agentes - ${ministerio}</title>
          <style>
            table { width: 100%; border-collapse: collapse; }
            th, td { border: 1px solid black; padding: 8px; text-align: left; }
            th { background-color: #8B4513; color: white; }
          </style>
        </head>
        <body>
          <h2>Reporte de Agentes - ${ministerio}</h2>
          <h3>Fecha: ${date}</h3>
          <table>
            <thead>
              <tr>
                <th>Nombre</th>
                <th>DPI</th>
                <th>No. Celular</th>
                <th>Comunidad</th>
                <th>Oratorio</th>
                <th>Tiempo de Servicio</th>
              </tr>
            </thead>
            <tbody>
              ${filteredAgents.map(agent => `
                <tr>
                  <td>${agent.nombre}</td>
                  <td>${agent.dpi}</td>
                  <td>${agent.celular}</td>
                  <td>${agent.comunidad}</td>
                  <td>${agent.oratorio}</td>
                  <td>${agent.tiempoServicio}</td>
                </tr>
              `).join('')}
            </tbody>
          </table>
        </body>
      </html>
    `;
    
    const printWindow = window.open('', '', 'height=600,width=800');
    printWindow.document.write(printContent);
    printWindow.document.close();
    printWindow.print();
  }
}

function showImportDialog() {
  Swal.fire({
    title: 'Importar Agentes desde Excel',
    html: `
      <div class="mb-3">
        <p>Por favor, asegúrese que su archivo Excel tenga las siguientes columnas:</p>
        <ul class="text-start">
          <li>Nombre</li>
          <li>DPI</li>
          <li>No. Celular</li>
          <li>Comunidad</li>
          <li>Oratorio</li>
          <li>Ministerio</li>
          <li>Fecha de Nacimiento (YYYY-MM-DD)</li>
          <li>Fecha de Inicio (YYYY-MM-DD)</li>
        </ul>
        <input type="file" class="form-control" id="excelFile" accept=".xlsx, .xls, .csv">
      </div>
    `,
    confirmButtonText: 'Importar',
    confirmButtonColor: '#8B4513',
    showCancelButton: true,
    cancelButtonText: 'Cancelar',
    width: '600px',
    preConfirm: () => {
      const file = document.getElementById('excelFile').files[0];
      if (!file) {
        Swal.showValidationMessage('Por favor seleccione un archivo');
        return false;
      }
      return file;
    }
  }).then((result) => {
    if (result.isConfirmed) {
      const file = result.value;
      processExcelFile(file);
    }
  });
}

function processExcelFile(file) {
  // Show loading state
  Swal.fire({
    title: 'Procesando archivo...',
    html: 'Por favor espere mientras se importan los datos',
    allowOutsideClick: false,
    didOpen: () => {
      Swal.showLoading();
    }
  });

  const reader = new FileReader();
  reader.onload = function(e) {
    const data = new Uint8Array(e.target.result);
    const workbook = XLSX.read(data, {type: 'array'});
    const firstSheet = workbook.Sheets[workbook.SheetNames[0]];
    const jsonData = XLSX.utils.sheet_to_json(firstSheet, {raw: true});

    const importResults = {
      success: 0,
      errors: [],
      total: jsonData.length
    };

    jsonData.forEach((row, index) => {
      try {
        // Validate required fields
        const requiredFields = ['Nombre', 'DPI', 'No. Celular', 'Comunidad', 'Oratorio', 'Ministerio'];
        const missingFields = requiredFields.filter(field => !row[field]);
        
        if (missingFields.length > 0) {
          throw new Error(`Fila ${index + 2}: Campos requeridos faltantes: ${missingFields.join(', ')}`);
        }

        // Validate ministerio exists
        if (!ministeriosDB.includes(row.Ministerio)) {
          throw new Error(`Fila ${index + 2}: Ministerio "${row.Ministerio}" no existe en el sistema`);
        }

        // Create agent object
        const agent = {
          nombre: row.Nombre,
          dpi: row.DPI.toString(),
          celular: row['No. Celular'].toString(),
          comunidad: row.Comunidad,
          oratorio: row.Oratorio,
          ministerio: row.Ministerio,
          fechaNacimiento: row['Fecha de Nacimiento'] || '',
          fechaInicio: row['Fecha de Inicio'] || new Date().toISOString().split('T')[0],
          tiempoServicio: calculateServiceTime(row['Fecha de Inicio'] || new Date().toISOString().split('T')[0]),
          hasLinkedRecords: false
        };

        agentesDB.push(agent);
        saveToLocalStorage(); // Save updated agents
        importResults.success++;
      } catch (error) {
        importResults.errors.push(error.message);
      }
    });

    // Update table and show results
    updateAgentsTable();
    
    Swal.fire({
      title: 'Importación Completada',
      html: `
        <div class="text-start">
          <p>Total de registros: ${importResults.total}</p>
          <p>Importados exitosamente: ${importResults.success}</p>
          <p>Errores: ${importResults.errors.length}</p>
          ${importResults.errors.length > 0 ? `
            <div class="mt-3">
              <h6>Detalles de errores:</h6>
              <ul>
                ${importResults.errors.map(error => `<li>${error}</li>`).join('')}
              </ul>
            </div>
          ` : ''}
        </div>
      `,
      icon: importResults.errors.length === 0 ? 'success' : 'warning',
      confirmButtonColor: '#8B4513'
    });
  };

  reader.readAsArrayBuffer(file);
}
</script></body></html>
